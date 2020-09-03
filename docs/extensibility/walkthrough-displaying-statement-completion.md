---
title: 'Procedura dettagliata: visualizzazione del completamento delle istruzioni | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 472ff8c10e1346f25e7bc72ed5fd4ee9f31bbafa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904785"
---
# <a name="walkthrough-display-statement-completion"></a>Procedura dettagliata: Visualizzare il completamento istruzioni
È possibile implementare il completamento delle istruzioni basate sul linguaggio definendo gli identificatori per i quali si desidera fornire il completamento e quindi attivare una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire l'estensione del nome di file e il tipo di contenuto e quindi visualizzare il completamento solo per quel tipo. In alternativa, è possibile attivare il completamento per un tipo di contenuto esistente, ad esempio "testo normale". In questa procedura dettagliata viene illustrato come attivare il completamento delle istruzioni per il tipo di contenuto "testo normale", che è il tipo di contenuto dei file di testo. Il tipo di contenuto "Text" è il predecessore di tutti gli altri tipi di contenuto, inclusi il codice e i file XML.

 Il completamento delle istruzioni viene in genere attivato digitando determinati caratteri, ad esempio digitando l'inizio di un identificatore, ad esempio "using". Viene in genere rilasciata premendo la **barra spaziatrice**, la **scheda**o il tasto **invio** per eseguire il commit di una selezione. È possibile implementare le funzionalità di IntelliSense che vengono attivate quando si digita un carattere usando un gestore di comando per le sequenze di tasti ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia) e un provider del gestore che implementa l' <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine di completamento, ovvero l'elenco di identificatori che partecipano al completamento, implementare l' <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaccia e un provider di origine di completamento ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaccia). I provider sono parti del componente Managed Extensibility Framework (MEF). Sono responsabili dell'esportazione delle classi di origine e del controller e dell'importazione di servizi e broker, ad esempio, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> che consente la navigazione nel buffer di testo e <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , che attiva la sessione di completamento.

 In questa procedura dettagliata viene illustrato come implementare il completamento delle istruzioni per un set hardcoded di identificatori. Nelle implementazioni complete, il servizio di linguaggio e la documentazione della lingua sono responsabili di fornire tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creare un progetto MEF

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `CompletionTest` .

2. Aggiungere un modello di elemento classificatore editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

4. Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** sia impostato su `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 15.0

     Microsoft. VisualStudio. Shell. Immutable. 10.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-the-completion-source"></a>Implementare l'origine di completamento
 L'origine di completamento è responsabile della raccolta del set di identificatori e dell'aggiunta del contenuto alla finestra di completamento quando un utente digita un trigger di completamento, ad esempio le prime lettere di un identificatore. In questo esempio, gli identificatori e le relative descrizioni sono hardcoded nel <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo. Nella maggior parte degli usi reali, si userà il parser del linguaggio per ottenere i token per popolare l'elenco di completamento.

### <a name="to-implement-the-completion-source"></a>Per implementare l'origine di completamento

1. Aggiungere un file di classe e assegnargli il nome `TestCompletionSource`.

2. Aggiungere le importazioni seguenti:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modificare la dichiarazione di classe per in `TestCompletionSource` modo da implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Aggiungere campi privati per il provider di origine, il buffer di testo e un elenco di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> oggetti (che corrispondono agli identificatori che parteciperanno alla sessione di completamento):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Aggiungere un costruttore che imposta il provider e il buffer di origine. La `TestCompletionSourceProvider` classe è definita nei passaggi successivi:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo aggiungendo un set di completamenti che contiene i completamenti che si desidera fornire nel contesto. Ogni set di completamenti contiene un set di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> completamenti e corrisponde a una scheda della finestra di completamento. Nei progetti Visual Basic le schede della finestra di completamento sono denominate **comuni** e **tutte**. Il `FindTokenSpanAtPosition` metodo viene definito nel passaggio successivo.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Il metodo seguente viene utilizzato per trovare la parola corrente dalla posizione del cursore:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implementare il `Dispose()` Metodo:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementare il provider di origine di completamento
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza dell'origine di completamento.

### <a name="to-implement-the-completion-source-provider"></a>Per implementare il provider di origine di completamento

1. Aggiungere una classe denominata `TestCompletionSourceProvider` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Esportare questa classe con un oggetto <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo normale" e un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "completamento del test".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importa un oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , che trova la parola corrente nell'origine di completamento.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodo per creare un'istanza dell'origine di completamento.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementare il provider del gestore del comando di completamento
 Il provider del gestore del comando di completamento è derivato da un oggetto <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , che è in attesa di un evento di creazione della visualizzazione di testo e converte la visualizzazione da un oggetto, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> che consente l'aggiunta del comando alla catena di comandi della shell di Visual Studio, a un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Poiché questa classe è un'esportazione MEF, è possibile utilizzarla anche per importare i servizi richiesti dal gestore comando stesso.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Per implementare il provider del gestore del comando di completamento

1. Aggiungere un file denominato `TestCompletionCommandHandler` .

2. Aggiungere le direttive using seguenti:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Aggiungere una classe denominata `TestCompletionHandlerProvider` che implementi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Esportare questa classe con un valore <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "gestore di completamento del token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo non crittografato" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importare la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , che consente la conversione da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a un, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> e un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> che consente l'accesso ai servizi standard di Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo per creare un'istanza del gestore del comando.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementare il gestore del comando di completamento
 Poiché il completamento delle istruzioni viene attivato dalle sequenze di tasti, è necessario implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per ricevere ed elaborare le sequenze di tasti che attivano, sottoporre a commit e ignorare la sessione di completamento.

#### <a name="to-implement-the-completion-command-handler"></a>Per implementare il gestore del comando di completamento

1. Aggiungere una classe denominata `TestCompletionCommandHandler` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Aggiungere campi privati per il gestore di comandi successivo (a cui si passa il comando), la visualizzazione di testo, il provider del gestore del comando (che consente l'accesso a vari servizi) e una sessione di completamento:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Aggiungere un costruttore che imposta la visualizzazione di testo e i campi del provider e aggiunge il comando alla catena di comandi:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo passando il comando insieme a:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve una sequenza di tasti, deve eseguire una delle operazioni seguenti:

   - Consentire la scrittura del carattere nel buffer e quindi attivare o filtrare il completamento. I caratteri di stampa eseguono questa operazione.

   - Eseguire il commit del completamento, ma non consentire la scrittura del carattere nel buffer. (Spazi vuoti, **Tab**e **invio** eseguire questa operazione quando viene visualizzata una sessione di completamento).

   - Consente di passare il comando al gestore successivo. (Tutti gli altri comandi).

     Poiché questo metodo può visualizzare l'interfaccia utente, chiamare <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> per assicurarsi che non venga chiamato in un contesto di automazione:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Questo codice è un metodo privato che attiva la sessione di completamento:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. L'esempio successivo è un metodo privato che annulla la sottoscrizione dell' <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Per compilare e testare la soluzione CompletionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include la parola "Add".

4. Quando si digita prima "a" e quindi "d", viene visualizzato un elenco che contiene "addizione" e "adattamento". Si noti che è selezionata l'opzione aggiunta. Quando si digita un'altra "d", l'elenco deve contenere solo "addizione", che ora è selezionato. È possibile eseguire il commit di "addizione" premendo la **barra spaziatrice**, la **scheda**o il tasto **invio** oppure chiudere l'elenco digitando ESC o qualsiasi altra chiave.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
