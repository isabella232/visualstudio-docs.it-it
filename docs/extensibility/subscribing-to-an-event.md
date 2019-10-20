---
title: Sottoscrizione di un evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647922"
---
# <a name="subscribing-to-an-event"></a>Sottoscrizione a un evento
In questa procedura dettagliata viene illustrato come creare una finestra degli strumenti che risponde agli eventi in una tabella documenti in esecuzione (RDT). Una finestra degli strumenti ospita un controllo utente che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> connette l'interfaccia agli eventi.

## <a name="prerequisites"></a>Prerequisites
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Sottoscrizione di eventi RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Per creare un'estensione con una finestra degli strumenti

1. Creare un progetto denominato **RDTExplorer** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **RDTExplorerWindow**.

     Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Per sottoscrivere gli eventi RDT

1. Aprire il file RDTExplorerWindowControl. XAML ed eliminare il pulsante denominato `button1`. Aggiungere un controllo <xref:System.Windows.Forms.ListBox> e accettare il nome predefinito. L'elemento Grid avrà un aspetto simile al seguente:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Aprire il file RDTExplorerWindow.cs nella visualizzazione codice. Aggiungere le direttive using seguenti all'inizio del file.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modificare la classe `RDTExplorerWindow` in modo che, oltre a derivare dalla classe <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, implementi l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementare l'interfaccia. Posizionare il cursore sul nome IVsRunningDocTableEvents. Nel margine sinistro dovrebbe essere visualizzata una lampadina. Fare clic sulla freccia in giù a destra della lampadina e selezionare **implementa interfaccia**.

5. In ogni metodo nell'interfaccia sostituire la riga `throw new NotImplementedException();` con la seguente:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Aggiungere un campo cookie alla classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Questo oggetto include il cookie restituito dal metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Eseguire l'override del metodo Initialize () di RDTExplorerWindow per registrare gli eventi RDT. È necessario ottenere sempre i servizi nel metodo Initialize () di ToolWindowPane, non nel costruttore.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> viene chiamato per ottenere un'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>. Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> connette gli eventi RDT a un oggetto che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, in questo caso un oggetto RDTExplorer.

8. Aggiornare il metodo Dispose () di RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> Elimina la connessione tra `RDTExplorer` e la notifica degli eventi RDT.

9. Aggiungere la riga seguente al corpo del gestore di <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>, immediatamente prima dell'istruzione `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Aggiungere una riga simile al corpo del gestore <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> e ad altri eventi che si desidera visualizzare nella casella di riepilogo.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.

12. Aprire **RDTExplorerWindow** (**View/other Windows/RDTExplorerWindow**).

     Viene visualizzata la finestra **RDTExplorerWindow** con un elenco di eventi vuoto.

13. Aprire o creare una soluzione.

     Quando vengono generati eventi `OnBeforeLastDocument` e `OnAfterFirstDocument`, la notifica di ogni evento viene visualizzata nell'elenco di eventi.
