---
title: Sottoscrizione di un evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699691"
---
# <a name="subscribing-to-an-event"></a>Sottoscrizione a un evento
In questa procedura dettagliata viene illustrato come creare una finestra degli strumenti che risponde agli eventi in una tabella documenti in esecuzione (RDT). Una finestra degli strumenti ospita un controllo utente che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette l'interfaccia agli eventi.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Sottoscrizione di eventi RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Per creare un'estensione con una finestra degli strumenti

1. Creare un progetto denominato **RDTExplorer** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **RDTExplorerWindow**.

     Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Per sottoscrivere gli eventi RDT

1. Aprire il file RDTExplorerWindowControl. XAML ed eliminare il pulsante denominato `button1` . Aggiungere un <xref:System.Windows.Forms.ListBox> controllo e accettare il nome predefinito. L'elemento Grid avrà un aspetto simile al seguente:

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

3. Modificare la `RDTExplorerWindow` classe in modo che, oltre a derivare dalla <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> classe, implementi l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfaccia.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementare l'interfaccia. Posizionare il cursore sul nome IVsRunningDocTableEvents. Nel margine sinistro dovrebbe essere visualizzata una lampadina. Fare clic sulla freccia in giù a destra della lampadina e selezionare **implementa interfaccia**.

5. In ogni metodo nell'interfaccia sostituire la riga `throw new NotImplementedException();` con:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Aggiungere un campo cookie alla classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Questo oggetto include il cookie restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo.

7. Eseguire l'override del metodo Initialize () di RDTExplorerWindow per registrare gli eventi RDT. È necessario ottenere sempre i servizi nel metodo Initialize () di ToolWindowPane, non nel costruttore.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> servizio viene chiamato per ottenere un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaccia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette gli eventi RDT a un oggetto che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> , in questo caso, un oggetto RDTExplorer.

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

     Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> metodo elimina la connessione tra `RDTExplorer` e la notifica degli eventi RDT.

9. Aggiungere la riga seguente al corpo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> gestore, immediatamente prima dell' `return` istruzione.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Aggiungere una riga simile al corpo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> gestore e ad altri eventi che si desidera visualizzare nella casella di riepilogo.

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

     Quando `OnBeforeLastDocument` `OnAfterFirstDocument` vengono generati gli eventi e, la notifica di ogni evento viene visualizzata nell'elenco di eventi.
