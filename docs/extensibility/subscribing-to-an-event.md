---
title: Sottoscrizione a un'istanza di | Microsoft Docs
description: Informazioni su come creare una finestra degli strumenti che risponde agli eventi in una tabella di documenti in esecuzione in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f35da7cb7b4129af3aaf6a3289cd2bb0c8b7d10e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117397"
---
# <a name="subscribing-to-an-event"></a>Sottoscrizione a un evento
Questa procedura dettagliata illustra come creare una finestra degli strumenti che risponde agli eventi in una tabella di documenti in esecuzione (RDT). Una finestra degli strumenti ospita un controllo utente che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette l'interfaccia agli eventi.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="subscribing-to-rdt-events"></a>Sottoscrizione a eventi RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Per creare un'estensione con una finestra degli strumenti

1. Creare un progetto denominato **RDTExplorer** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **RDTExplorerWindow.**

     Per altre informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creazione di un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

#### <a name="to-subscribe-to-rdt-events"></a>Per sottoscrivere eventi RDT

1. Aprire il file RDTExplorerWindowControl.xaml ed eliminare il pulsante denominato `button1` . Aggiungere un <xref:System.Windows.Forms.ListBox> controllo e accettare il nome predefinito. L'elemento Grid dovrebbe essere simile al seguente:

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

3. Modificare la classe in modo che, oltre `RDTExplorerWindow` a derivare dalla classe , <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> l'interfaccia .

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementare l'interfaccia . Posizionare il cursore sul nome IVsRunningDocTableEvents. Verrà visualizzata una lampadina nel margine sinistro. Fare clic sulla freccia GIÙ a destra della lampadina e selezionare **Implementa interfaccia.**

5. In ogni metodo nell'interfaccia sostituire la riga `throw new NotImplementedException();` con la seguente:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Aggiungere un campo cookie alla classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Contiene il cookie restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo .

7. Eseguire l'override del metodo Initialize() di RDTExplorerWindow per eseguire la registrazione per gli eventi RDT. È consigliabile ottenere sempre i servizi nel metodo Initialize() di ToolWindowPane, non nel costruttore.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> servizio viene chiamato per ottenere un'interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette gli eventi RDT a un oggetto che implementa , in questo caso un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> RDTExplorer.

8. Aggiornare il metodo Dispose() di RDTExplorerWindow.

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

     Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> metodo elimina la connessione tra e la notifica degli eventi `RDTExplorer` RDT.

9. Aggiungere la riga seguente al corpo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> gestore, subito prima dell'istruzione `return` .

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Aggiungere una riga simile al corpo del gestore e ad altri eventi che <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> si desidera visualizzare nella casella di riepilogo.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compilare il progetto e avviare il debug. Verrà visualizzata Visual Studio'istanza sperimentale.

12. Aprire **RDTExplorerWindow** **(Visualizza/Altro Windows/RDTExplorerWindow**).

     Verrà **visualizzata la finestra RDTExplorerWindow** con un elenco di eventi vuoto.

13. Aprire o creare una soluzione.

     Quando `OnBeforeLastDocument` vengono generati gli eventi e , la notifica di ogni evento viene visualizzata `OnAfterFirstDocument` nell'elenco di eventi.
