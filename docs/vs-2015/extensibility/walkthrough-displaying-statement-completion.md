---
title: 'Procedura dettagliata: Visualizzazione del completamento istruzioni | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 097cb671e15b75edd7e61f7860cf3a0c03123c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733042"
---
# <a name="walkthrough-displaying-statement-completion"></a>Procedura dettagliata: visualizzazione del completamento istruzioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile implementare il completamento delle istruzioni basata sul linguaggio definendo gli identificatori per il quale si desidera fornire il completamento e quindi attivare una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire il proprio estensione di file e il tipo di contenuto e quindi visualizzare il completamento per solo tale tipo oppure è possibile attivare il completamento di un tipo di contenuto esistente, ad esempio, "normale". Questa procedura dettagliata illustra come attivare il completamento delle istruzioni per il tipo di contenuto "testo normale", ovvero il tipo di contenuto dei file di testo. Il tipo di contenuto "text" è il predecessore di tutti gli altri tipi contenuti, inclusi file XML e codice.  
  
 Completamento delle istruzioni viene in genere attivato digitando determinati caratteri, ad esempio, digitando l'inizio di un identificatore, ad esempio "using". Viene chiuso in genere premendo il tasto Tab, barra spaziatrice o INVIO per eseguire il commit di una selezione. È possibile implementare le funzionalità di IntelliSense che vengono attivate digitando un carattere con un gestore di comandi per le sequenze di tasti (il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e un provider del gestore che implementa il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine di completamento, ovvero l'elenco degli identificatori che fanno parte di completamento, implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaccia e un provider di origine di completamento (il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface). I provider sono parti componente Managed Extensibility Framework (MEF). Sono responsabili per importare servizi e Broker ed esportare le classi di origine e il controller, ad esempio, il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente la navigazione nel buffer di testo e il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, che attiva la sessione di completamento.  
  
 Questa procedura dettagliata viene illustrato come implementare il completamento delle istruzioni per un set di identificatori a livello di codice. In implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabile di fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `CompletionTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** è impostata su `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Implementazione di origine di completamento  
 L'origine di completamento è responsabile per la raccolta di set di identificatori e aggiungere il contenuto nella finestra di completamento quando un utente digita un trigger di completamento, ad esempio le prime lettere di un identificatore. In questo esempio, gli identificatori e le relative descrizioni sono impostati come hardcoded nel <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> (metodo). Nella maggior parte dei casi reali, si utilizzerebbe il parser del linguaggio per ottenere i token per popolare l'elenco di completamento.  
  
#### <a name="to-implement-the-completion-source"></a>Per implementare l'origine di completamento  
  
1.  Aggiungere un file di classe e assegnargli il nome `TestCompletionSource`.  
  
2.  Aggiungere queste istruzioni import:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  Modificare la dichiarazione di classe per `TestCompletionSource` in modo che possa implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  Aggiungere campi privati per il provider dell'origine, il buffer di testo e un elenco di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> oggetti (che corrispondono agli identificatori che faranno parte della sessione di completamento):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  Aggiungere un costruttore che imposta il buffer e il provider del codice sorgente. Il `TestCompletionSourceProvider` classe è definita nei passaggi successivi:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo aggiungendo un set di completamenti che contiene i completamenti che si desidera offrire nel contesto. Ogni set di completamento contiene un set di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> completamenti e corrisponde a una scheda della finestra di completamento. (Nei progetti Visual Basic, le schede delle finestre di completamento sono denominati **comuni** e **tutte**.) Il metodo FindTokenSpanAtPosition è definito nel passaggio successivo.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  Il metodo seguente viene usato per trovare la parola corrente dalla posizione del cursore:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  Implementare il `Dispose()` metodo:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementazione del Provider di origine di completamento  
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza di origine di completamento.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Per implementare il provider di origine di completamento  
  
1.  Aggiungere una classe denominata `TestCompletionSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Esportare questa classe con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo normale" e un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "completamento test".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  Importa un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente di trovare la parola corrente nell'origine di completamento.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodo per creare un'istanza di origine di completamento.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementazione di un Provider del gestore comando completamento  
 Il provider del gestore comando completamento è derivato da un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, che è in attesa di un evento di creazione della visualizzazione di testo e consente di convertire la visualizzazione da un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, che consente l'aggiunta del comando alla catena del comando della shell di Visual Studio, per un' <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Poiché questa classe è un'esportazione MEF, è possibile usarlo anche per importare i servizi necessari per il gestore del comando stesso.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Per implementare il provider di gestore di comando di completamento  
  
1.  Aggiungere un file denominato `TestCompletionCommandHandler`.  
  
2.  Aggiungere le istruzioni using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  Aggiungere una classe denominata `TestCompletionHandlerProvider` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Esportare questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "gestore completamento token", una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo normale" e una <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  Importa il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, che consente la conversione da un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, una <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>e un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> che abilita l'accesso a servizi di Visual Studio standard.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo per creare un'istanza il gestore del comando.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementazione del gestore di comando di completamento  
 Poiché il completamento delle istruzioni viene attivato da sequenze di tasti, è necessario implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per ricevere ed elaborare le pressioni di tasti che attivano, eseguire il commit e chiudere la sessione di completamento.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Per implementare il gestore di comando di completamento  
  
1. Aggiungere una classe denominata `TestCompletionCommandHandler` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Aggiungere campi privati per il gestore del comando successivo (a cui è passare il comando), la visualizzazione di testo, il provider del gestore di comando (che consente l'accesso a vari servizi) e una sessione di completamento:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Aggiungere un costruttore che imposta la visualizzazione di testo e i campi del provider e aggiunge il comando alla catena del comando:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo passando il comando lungo:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve una sequenza di tasti, è necessario eseguire una di queste operazioni:  
  
   - Consenti il carattere da scrivere nel buffer e quindi attivare o filtro di completamento. (Caratteri stampabili fare questo).  
  
   - Eseguire il commit del completamento, ma non consentono il carattere da scrivere nel buffer. (Lo spazio vuoto, Tab e invio farlo durante una sessione di completamento viene visualizzata.)  
  
   - Consenti il comando deve essere passato gestore successivo. (Tutti gli altri comandi.)  
  
     Poiché questo metodo può visualizzare l'interfaccia utente, chiamare il metodo <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> per assicurarsi che non viene chiamato in un contesto di automazione:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Questo codice è un metodo privato che attiva la sessione di completamento:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. L'esempio successivo è un metodo privato che annulla la sottoscrizione di <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Per compilare e testare la soluzione CompletionTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include la parola "Aggiungi".  
  
4.  Mentre si digita prima di tutto "a" e quindi "d", verrà visualizzato un elenco che contiene "addition" e "personalizzazione". Si noti che sia selezionata l'addizione. Quando si digita un'altra "d", l'elenco deve contenere solo "addition," che viene ora selezionato. È possibile eseguire il commit premendo il tasto Tab, barra spaziatrice o invio "addition" o ignorare l'elenco digitando Esc o qualsiasi altra chiave.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

