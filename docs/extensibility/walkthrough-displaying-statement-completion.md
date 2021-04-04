---
title: 'Procedura dettagliata: visualizzazione del completamento delle istruzioni | Microsoft Docs'
description: Informazioni su come implementare il completamento delle istruzioni basato sul linguaggio per il contenuto non crittografato usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: leslierichardson95
ms.author: lerich
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 51281c261baf5744c1d3aa0903985a173ff240f2
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217476"
---
# <a name="walkthrough-display-statement-completion"></a>Procedura dettagliata: Visualizzare il completamento istruzioni
È possibile implementare il completamento delle istruzioni basate sul linguaggio definendo gli identificatori per i quali si desidera fornire il completamento e quindi attivare una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire l'estensione del nome di file e il tipo di contenuto e quindi visualizzare il completamento solo per quel tipo. In alternativa, è possibile attivare il completamento per un tipo di contenuto esistente, ad esempio "testo normale". In questa procedura dettagliata viene illustrato come attivare il completamento delle istruzioni per il tipo di contenuto "testo normale", che è il tipo di contenuto dei file di testo. Il tipo di contenuto "Text" è il predecessore di tutti gli altri tipi di contenuto, inclusi il codice e i file XML.

 Il completamento delle istruzioni viene in genere attivato digitando determinati caratteri, ad esempio digitando l'inizio di un identificatore, ad esempio "using". Viene in genere rilasciata premendo la **barra spaziatrice**, la **scheda** o il tasto **invio** per eseguire il commit di una selezione. È possibile implementare le funzionalità di IntelliSense che vengono attivate quando si digita un carattere usando un gestore di comando per le sequenze di tasti ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia) e un provider del gestore che implementa l' <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine di completamento, ovvero l'elenco di identificatori che partecipano al completamento, implementare l' <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaccia e un provider di origine di completamento ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interfaccia). I provider sono parti del componente Managed Extensibility Framework (MEF). Sono responsabili dell'esportazione delle classi di origine e del controller e dell'importazione di servizi e broker, ad esempio, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> che consente la navigazione nel buffer di testo e <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , che attiva la sessione di completamento.

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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet1":::

3. Modificare la dichiarazione di classe per in `TestCompletionSource` modo da implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet2":::

4. Aggiungere campi privati per il provider di origine, il buffer di testo e un elenco di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> oggetti (che corrispondono agli identificatori che parteciperanno alla sessione di completamento):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet3":::

5. Aggiungere un costruttore che imposta il provider e il buffer di origine. La `TestCompletionSourceProvider` classe è definita nei passaggi successivi:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet4":::

6. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo aggiungendo un set di completamenti che contiene i completamenti che si desidera fornire nel contesto. Ogni set di completamenti contiene un set di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> completamenti e corrisponde a una scheda della finestra di completamento. Nei progetti Visual Basic le schede della finestra di completamento sono denominate **comuni** e **tutte**. Il `FindTokenSpanAtPosition` metodo viene definito nel passaggio successivo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet5":::

7. Il metodo seguente viene utilizzato per trovare la parola corrente dalla posizione del cursore:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet6":::

8. Implementare il `Dispose()` Metodo:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet7":::

## <a name="implement-the-completion-source-provider"></a>Implementare il provider di origine di completamento
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza dell'origine di completamento.

### <a name="to-implement-the-completion-source-provider"></a>Per implementare il provider di origine di completamento

1. Aggiungere una classe denominata `TestCompletionSourceProvider` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Esportare questa classe con un oggetto <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo normale" e un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "completamento del test".

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet8":::

2. Importa un oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , che trova la parola corrente nell'origine di completamento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet9":::

3. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodo per creare un'istanza dell'origine di completamento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet10":::

## <a name="implement-the-completion-command-handler-provider"></a>Implementare il provider del gestore del comando di completamento
 Il provider del gestore del comando di completamento è derivato da un oggetto <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , che è in attesa di un evento di creazione della visualizzazione di testo e converte la visualizzazione da un oggetto, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> che consente l'aggiunta del comando alla catena di comandi della shell di Visual Studio, a un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Poiché questa classe è un'esportazione MEF, è possibile utilizzarla anche per importare i servizi richiesti dal gestore comando stesso.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Per implementare il provider del gestore del comando di completamento

1. Aggiungere un file denominato `TestCompletionCommandHandler` .

2. Aggiungere le direttive using seguenti:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet11":::

3. Aggiungere una classe denominata `TestCompletionHandlerProvider` che implementi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Esportare questa classe con un valore <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "gestore di completamento del token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo non crittografato" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet12":::

4. Importare la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , che consente la conversione da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a un, <xref:Microsoft.VisualStudio.Text.Editor.ITextView> un <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> e un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> che consente l'accesso ai servizi standard di Visual Studio.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet13":::

5. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo per creare un'istanza del gestore del comando.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet14":::

## <a name="implement-the-completion-command-handler"></a>Implementare il gestore del comando di completamento
 Poiché il completamento delle istruzioni viene attivato dalle sequenze di tasti, è necessario implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per ricevere ed elaborare le sequenze di tasti che attivano, sottoporre a commit e ignorare la sessione di completamento.

#### <a name="to-implement-the-completion-command-handler"></a>Per implementare il gestore del comando di completamento

1. Aggiungere una classe denominata `TestCompletionCommandHandler` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet15":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet15":::

2. Aggiungere campi privati per il gestore di comandi successivo (a cui si passa il comando), la visualizzazione di testo, il provider del gestore del comando (che consente l'accesso a vari servizi) e una sessione di completamento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet16":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet16":::

3. Aggiungere un costruttore che imposta la visualizzazione di testo e i campi del provider e aggiunge il comando alla catena di comandi:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet17":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet17":::

4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo passando il comando insieme a:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet18":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet18":::

5. Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve una sequenza di tasti, deve eseguire una delle operazioni seguenti:

   - Consentire la scrittura del carattere nel buffer e quindi attivare o filtrare il completamento. I caratteri di stampa eseguono questa operazione.

   - Eseguire il commit del completamento, ma non consentire la scrittura del carattere nel buffer. (Spazi vuoti, **Tab** e **invio** eseguire questa operazione quando viene visualizzata una sessione di completamento).

   - Consente di passare il comando al gestore successivo. (Tutti gli altri comandi).

     Poiché questo metodo può visualizzare l'interfaccia utente, chiamare <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> per assicurarsi che non venga chiamato in un contesto di automazione:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet19":::

6. Questo codice è un metodo privato che attiva la sessione di completamento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet20":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet20":::

7. L'esempio successivo è un metodo privato che annulla la sottoscrizione dell' <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet21":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet21":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Per compilare e testare la soluzione CompletionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include la parola "Add".

4. Quando si digita prima "a" e quindi "d", viene visualizzato un elenco che contiene "addizione" e "adattamento". Si noti che è selezionata l'opzione aggiunta. Quando si digita un'altra "d", l'elenco deve contenere solo "addizione", che ora è selezionato. È possibile eseguire il commit di "addizione" premendo la **barra spaziatrice**, la **scheda** o il tasto **invio** oppure chiudere l'elenco digitando ESC o qualsiasi altra chiave.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
