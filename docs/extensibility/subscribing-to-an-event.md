---
title: Sottoscrizione di un evento Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699691"
---
# <a name="subscribing-to-an-event"></a>Sottoscrizione a un evento
In questa procedura dettagliata viene illustrato come creare una finestra degli strumenti che risponde agli eventi in una tabella documenti in esecuzione (RDT). Una finestra degli strumenti ospita <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>un controllo utente che implementa . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette l'interfaccia agli eventi.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="subscribing-to-rdt-events"></a>Sottoscrizione di eventi RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Per creare un'estensione con una finestra degli strumentiTo create an extension with a tool window

1. Creare un progetto denominato **RDTExplorer** utilizzando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **RDTExplorerWindow**.

     Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Per sottoscrivere gli eventi RDT

1. Aprire il file RDTExplorerWindowControl.xaml ed `button1`eliminare il pulsante denominato . Aggiungere <xref:System.Windows.Forms.ListBox> un controllo e accettare il nome predefinito. L'elemento Grid dovrebbe essere simile al seguente:The Grid element should look like this:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Aprire il file RDTExplorerWindow.cs nella vista codice. Aggiungere le direttive using seguenti all'inizio del file.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modificare `RDTExplorerWindow` la classe in modo che, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> oltre a derivare dalla classe, implementi l'interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implementare l'interfaccia. Posizionare il cursore sul iVsRunningDocTableEvents nome. Dovresti vedere una lampadina nel margine sinistro. Fare clic sulla freccia Giù a destra della lampadina e selezionare **Implementa interfaccia**.

5. In ogni metodo nell'interfaccia, `throw new NotImplementedException();` sostituire la riga con il seguente:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Aggiungere un campo cookie alla classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Contiene il cookie restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo.

7. Eseguire l'override del metodo Initialize() di RDTExplorerWindow per eseguire la registrazione per gli eventi RDT. È sempre necessario ottenere i servizi nel metodo Initialize() di ToolWindowPane, non nel costruttore.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> servizio viene chiamato <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> per ottenere un'interfaccia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette gli eventi RDT <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>a un oggetto che implementa , in questo caso, un oggetto RDTExplorer.

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

     Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> metodo elimina la `RDTExplorer` connessione tra e notifica dell'evento RDT.

9. Aggiungere la riga seguente al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> corpo del `return` gestore, appena prima dell'istruzione.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Aggiungere una riga simile al <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> corpo del gestore e ad altri eventi che si desidera visualizzare nella casella di riepilogo.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.The Visual Studio experimental instance appears.

12. Aprire **RDTExplorerWindow** (**Visualizza / Altro Windows / RDTExplorerWindow**).

     Verrà visualizzata la finestra **RDTExplorerWindow** con un elenco di eventi vuoto.

13. Aprire o creare una soluzione.

     Man `OnBeforeLastDocument` `OnAfterFirstDocument` mano che gli eventi vengono generati, nell'elenco degli eventi viene visualizzata la notifica di ogni evento.
