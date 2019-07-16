---
title: Sottoscrizione a un evento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 324e74c78f01da47c544b5f640ad0bd9052a1bb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160552"
---
# <a name="subscribing-to-an-event"></a>Sottoscrizione a un evento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare una finestra degli strumenti che risponde agli eventi in una tabella documenti in esecuzione (RDT). Una finestra degli strumenti contiene un controllo utente che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo connette l'interfaccia per gli eventi.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>Sottoscrizione di eventi RDT  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Per creare un'estensione con una finestra degli strumenti  
  
1. Creare un progetto denominato **RDTExplorer** usando il modello di progetto VSIX e aggiungere un modello di elemento di finestra degli strumenti personalizzata denominato **RDTExplorerWindow**.  
  
     Per altre informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
#### <a name="to-subscribe-to-rdt-events"></a>Per sottoscrivere gli eventi RDT  
  
1. Aprire il file RDTExplorerWindowControl.xaml ed eliminare il pulsante denominato `button1`. Aggiungere un <xref:System.Windows.Forms.ListBox> controllano e accettare il nome predefinito. L'elemento Grid dovrebbe essere simile al seguente:  
  
    ```xml  
    <Grid>  
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">  
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>  
            <ListBox x:Name="listBox" Height="100" />  
        </StackPanel>  
    </Grid>  
    ```  
  
2. Aprire il file RDTExplorerWindow.cs nella visualizzazione codice. Aggiungere le seguenti istruzioni using all'inizio del file.  
  
    ```csharp  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3. Modificare il `RDTExplorerWindow` classe operazione che, oltre che deriva dal <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> (classe), implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> interfaccia.  
  
    ```csharp  
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents  
    {. . .}  
    ```  
  
4. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.  
  
    - Implementare l'interfaccia. Posizionare il cursore sul nome IVsRunningDocTableEvents. Verrà visualizzata una lampadina nel margine sinistro. Fare clic sulla freccia verso il basso a destra della lampadina e selezionare **implementa interfaccia**.  
  
5. In ogni metodo nell'interfaccia, sostituire la riga `throw new NotImplementedException();` con questo:  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
6. Aggiungere un campo di cookie per la classe RDTExplorerWindow.  
  
    ```csharp  
    private uint rdtCookie;   
    ```  
  
     Questo file contiene il cookie restituito dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> (metodo).  
  
7. Eseguire l'override di metodo Initialize () del RDTExplorerWindow per registrare gli eventi RDT. È necessario ottenere servizi sempre nel metodo Initialize () del ToolWindowPane, non nel costruttore.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)  
        this.GetService(typeof(SVsRunningDocumentTable));  
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);  
    }  
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> servizio viene chiamato per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaccia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> metodo di eventi RDT si connette a un oggetto che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, in questo caso, un oggetto RDTExplorer.  
  
8. Metodo Dispose () del RDTExplorerWindow Update.  
  
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
  
     Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> metodo elimina la connessione tra `RDTExplorer` e notifica degli eventi RDT.  
  
9. Aggiungere la riga seguente nel corpo della <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> gestore, appena prima di `return` istruzione.  
  
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
  
12. Aprire il **RDTExplorerWindow** (**visualizzazione / altri Windows / RDTExplorerWindow**).  
  
     Il **RDTExplorerWindow** verrà visualizzata la finestra con un elenco di eventi vuoto.  
  
13. Aprire o creare una soluzione.  
  
     Come `OnBeforeLastDocument` e `OnAfterFirstDocument` gli eventi vengono attivati, notifica di ogni evento viene visualizzata nell'evento di elenco.
