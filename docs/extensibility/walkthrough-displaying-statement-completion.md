---
title: 'Procedura dettagliata: visualizzazione del completamento delle istruzioni Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697405"
---
# <a name="walkthrough-display-statement-completion"></a>Procedura dettagliata: Visualizzare il completamento istruzioni
È possibile implementare il completamento delle istruzioni basato sul linguaggio definendo gli identificatori per i quali si desidera fornire il completamento e quindi attivando una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire l'estensione e il tipo di contenuto personalizzati e quindi visualizzare il completamento solo per quel tipo. In alternativa, è possibile attivare il completamento per un tipo di contenuto esistente, ad esempio "testo normale". In questa procedura dettagliata viene illustrato come attivare il completamento delle istruzioni per il tipo di contenuto "testo normale", ovvero il tipo di contenuto dei file di testo. Il tipo di contenuto "testo" è il predecessore di tutti gli altri tipi di contenuto, inclusi i file di codice e XML.

 Il completamento delle istruzioni viene in genere attivato digitando determinati caratteri, ad esempio digitando l'inizio di un identificatore, ad esempio "using". In genere viene chiuso premendo la **barra spaziatrice,** **TAB**o **INVIO** per confermare una selezione. È possibile implementare le funzionalità di IntelliSense che attivano quando si <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> digita un carattere utilizzando <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> un gestore di comando per le sequenze di tasti (l'interfaccia) e un provider di gestori che implementa l'interfaccia. Per creare l'origine di completamento, ovvero l'elenco <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> di identificatori che partecipano al completamento, implementare l'interfaccia e un provider di origine di completamento (l'interfaccia). <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> I provider sono parti di componenti Managed Extensibility Framework (MEF). Sono responsabili dell'esportazione delle classi di origine e controller e dell'importazione di servizi e broker, ad esempio , <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>che consente la navigazione nel buffer di testo, e <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>di , che attiva la sessione di completamento.

 In questa procedura dettagliata viene illustrato come implementare il completamento delle istruzioni per un set di identificatori hardcoded. Nelle implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili della fornitura di tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `CompletionTest`la soluzione .

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

4. Aggiungere i seguenti riferimenti al progetto e assicurarsi `false`che **CopyLocal** sia impostato su :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementare l'origine di completamentoImplement the completion source
 L'origine di completamento è responsabile della raccolta del set di identificatori e dell'aggiunta del contenuto alla finestra di completamento quando un utente digita un trigger di completamento, ad esempio le prime lettere di un identificatore. In questo esempio, gli identificatori e le relative <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> descrizioni sono hardcoded nel metodo. Nella maggior parte degli usi reali, è necessario utilizzare il parser del linguaggio per ottenere i token per popolare l'elenco di completamento.

### <a name="to-implement-the-completion-source"></a>Per implementare l'origine di completamentoTo implement the completion source

1. Aggiungere un file di classe e assegnargli il nome `TestCompletionSource`.

2. Aggiungere queste importazioni:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modificare la dichiarazione di classe per `TestCompletionSource` in modo che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Aggiungere campi privati per il provider di origine, <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> il buffer di testo e un elenco di oggetti (che corrispondono agli identificatori che faranno parte della sessione di completamento):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Aggiungere un costruttore che imposta il provider di origine e il buffer. La `TestCompletionSourceProvider` classe viene definita nei passaggi successivi:The class is defined in later steps:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> il metodo aggiungendo un set di completamento che contiene i completamenti che si desidera fornire nel contesto. Ogni set di completamento contiene un set di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> completamenti e corrisponde a una scheda della finestra di completamento. Nei progetti Visual Basic le schede della finestra di completamento sono denominate **Comune (Tutti)** (Tutti). **All** Il `FindTokenSpanAtPosition` metodo viene definito nel passaggio successivo.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Il metodo seguente viene utilizzato per trovare la parola corrente dalla posizione del cursore:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implementare `Dispose()` il metodo:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementare il provider dell'origine di completamentoImplement the completion source provider
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza dell'origine di completamento.

### <a name="to-implement-the-completion-source-provider"></a>Per implementare il provider dell'origine di completamentoTo implement the completion source provider

1. Aggiungere una `TestCompletionSourceProvider` classe <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>denominata che implementa . Esportare questa <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> classe con un "testo semplice" e un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "completamento test".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>un oggetto , che trova la parola corrente nell'origine di completamento.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> il metodo per creare un'istanza dell'origine di completamento.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementare il provider del gestore del comando di completamentoImplement the completion command handler provider
 Il provider del gestore <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>comandi di completamento è derivato da un oggetto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, che è in ascolto di un evento di <xref:Microsoft.VisualStudio.Text.Editor.ITextView>creazione della visualizzazione di testo e converte la visualizzazione da un oggetto , che consente l'aggiunta del comando alla catena di comandi della shell di Visual Studio in un oggetto . Poiché questa classe è un'esportazione MEF, è anche possibile utilizzarla per importare i servizi richiesti dal gestore di comando stesso.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Per implementare il provider del gestore del comando di completamentoTo implement the completion command handler provider

1. Aggiungere un `TestCompletionCommandHandler`file denominato .

2. Aggiungere queste direttive using:Add these using directives:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Aggiungere una `TestCompletionHandlerProvider` classe <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>denominata che implementa . Esportare questa <xref:Microsoft.VisualStudio.Utilities.NameAttribute> classe con un "gestore di completamento del token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo/chiaro" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importare <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>l'oggetto , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> che <xref:Microsoft.VisualStudio.Text.Editor.ITextView>consente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>la conversione da un oggetto , un oggetto e un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> oggetto che consente l'accesso ai servizi standard di Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implementare <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> il metodo per creare un'istanza del gestore del comando.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementare il gestore del comando di completamentoImplement the completion command handler
 Poiché il completamento delle istruzioni viene attivato <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> da sequenze di tasti, è necessario implementare l'interfaccia per ricevere ed elaborare le sequenze di tasti che attivano, eseguono il commit e ignorano la sessione di completamento.

#### <a name="to-implement-the-completion-command-handler"></a>Per implementare il gestore del comando di completamentoTo implement the completion command handler

1. Aggiungere una `TestCompletionCommandHandler` classe <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>denominata che implementa :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Aggiungere campi privati per il gestore di comandi successivo (a cui si passa il comando), la visualizzazione di testo, il provider del gestore di comandi (che consente l'accesso a vari servizi) e una sessione di completamento:Add private fields for the next command handler (to which you pass the command), the text view, the command handler provider (which enables access to various services), and a completion session:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Aggiungere un costruttore che imposta la visualizzazione di testo e i campi del provider e aggiunge il comando alla catena di comandi:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo passando il comando lungo:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve una sequenza di tasti, deve eseguire una delle operazioni seguenti:When this method receives a keystroke, it must do one of these things:

   - Consentire la scrittura del carattere nel buffer e quindi attivare o filtrare il completamento. (I caratteri di stampa fanno questo.)

   - Eseguire il commit del completamento, ma non consentire la scrittura del carattere nel buffer. (Whitespace, **Tab**e **Enter** eseguire questa operazione quando viene visualizzata una sessione di completamento).

   - Consentire il passaggio del comando al gestore successivo. (Tutti gli altri comandi.)

     Poiché questo metodo può <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> visualizzare l'interfaccia utente, chiamare per assicurarsi che non viene chiamato in un contesto di automazione:Because this method may display UI, call to make sure that it's not called in an automation context:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Questo codice è un metodo privato che attiva la sessione di completamento:This code is a private method that triggers the completion session:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. L'esempio successivo è un metodo privato <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> che annulla la sottoscrizione all'evento:The next example is a private method that unsubscribes from the event:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Per compilare e testare la soluzione CompletionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare del testo che includa la parola "add".

4. Quando si digita prima "a" e poi "d", dovrebbe apparire un elenco che contiene "addition" e "adaptation". Si noti che l'addizione è selezionata. Quando si digita un'altra "d", l'elenco deve contenere solo "aggiunta", che è ora selezionata. È possibile eseguire il commit dell'"aggiunta" premendo la **barra spaziatrice**, **TAB**o **INVIO** oppure chiudere l'elenco digitando ESC o qualsiasi altro tasto.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
