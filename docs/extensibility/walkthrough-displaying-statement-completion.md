---
title: 'Procedura dettagliata: Visualizzazione del completamento delle istruzioni | Microsoft Docs'
description: Informazioni su come implementare il completamento delle istruzioni basate sul linguaggio per il contenuto in testo non crittografato usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 8dfea0b39cfeaccd01bde21d838a8f611a6b009a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049038"
---
# <a name="walkthrough-display-statement-completion"></a>Procedura dettagliata: Visualizzare il completamento istruzioni
È possibile implementare il completamento delle istruzioni basate sul linguaggio definendo gli identificatori per cui si vuole fornire il completamento e quindi attivando una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire l'estensione e il tipo di contenuto del nome file e quindi visualizzare il completamento solo per quel tipo. In caso contrario, è possibile attivare il completamento per un tipo di contenuto esistente, ad esempio "testo non crittografato". Questa procedura dettagliata illustra come attivare il completamento delle istruzioni per il tipo di contenuto "testo non crittografato", ovvero il tipo di contenuto dei file di testo. Il tipo di contenuto "text" è il predecessore di tutti gli altri tipi di contenuto, inclusi il codice e i file XML.

 Il completamento delle istruzioni viene in genere attivato digitando determinati caratteri, ad esempio digitando l'inizio di un identificatore, ad esempio "using". Viene in genere ignorata premendo la barra **spaziatrice,** **tab** o **INVIO** per eseguire il commit di una selezione. È possibile implementare le funzionalità IntelliSense che si attivano quando si digita un carattere usando un gestore di comandi per le sequenze di tasti (l'interfaccia ) e un provider di gestori che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> l'interfaccia . Per creare l'origine di completamento, ovvero l'elenco di identificatori che partecipano al completamento, implementare l'interfaccia e un provider di <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> origine di completamento (l'interfaccia <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> ). I provider sono Managed Extensibility Framework componenti (MEF). Sono responsabili dell'esportazione delle classi di origine e controller e dell'importazione di servizi e broker, ad esempio , che consente lo spostamento nel buffer di testo e , che attiva la sessione <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> di completamento.

 Questa procedura dettagliata illustra come implementare il completamento delle istruzioni per un set hard-coded di identificatori. Nelle implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili di fornire tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un file MEF Project

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Nuovo Project** selezionare Visual **C# /Extensibility** e quindi **VSIX Project**. Assegnare alla soluzione il nome `CompletionTest` .

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

4. Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** sia impostato su `false` :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementare l'origine di completamento
 L'origine di completamento è responsabile della raccolta del set di identificatori e dell'aggiunta del contenuto alla finestra di completamento quando un utente specifica un trigger di completamento, ad esempio le prime lettere di un identificatore. In questo esempio gli identificatori e le relative descrizioni sono hard-coded nel <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo . Nella maggior parte degli usi reali, si userebbe il parser del linguaggio per ottenere i token per popolare l'elenco di completamento.

### <a name="to-implement-the-completion-source"></a>Per implementare l'origine di completamento

1. Aggiungere un file di classe e assegnargli il nome `TestCompletionSource`.

2. Aggiungere queste importazioni:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet1":::

3. Modificare la dichiarazione di classe `TestCompletionSource` per in modo che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet2":::

4. Aggiungere campi privati per il provider di origine, il buffer di testo e un elenco di oggetti (che corrispondono agli identificatori che <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> parteciperanno alla sessione di completamento):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet3":::

5. Aggiungere un costruttore che imposta il provider di origine e il buffer. La `TestCompletionSourceProvider` classe viene definita nei passaggi successivi:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet4":::

6. Implementare il metodo aggiungendo un set di completamento che <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> contiene i completamenti da fornire nel contesto. Ogni set di completamento contiene un set <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> di completamenti e corrisponde a una scheda della finestra di completamento. Nei progetti Visual Basic, le schede della finestra di completamento sono denominate **Common** e **All.** Il `FindTokenSpanAtPosition` metodo viene definito nel passaggio successivo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet5":::

7. Il metodo seguente viene usato per trovare la parola corrente dalla posizione del cursore:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet6":::

8. Implementare il `Dispose()` metodo :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet7":::

## <a name="implement-the-completion-source-provider"></a>Implementare il provider di origine di completamento
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza dell'origine di completamento.

### <a name="to-implement-the-completion-source-provider"></a>Per implementare il provider di origine di completamento

1. Aggiungere una classe denominata `TestCompletionSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Esportare questa classe con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> valore di "testo non crittografato" e <xref:Microsoft.VisualStudio.Utilities.NameAttribute> un valore di "completamento test".

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet8":::

2. Importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> un oggetto , che trova la parola corrente nell'origine di completamento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet9":::

3. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodo per creare un'istanza dell'origine di completamento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb" id="Snippet10":::

## <a name="implement-the-completion-command-handler-provider"></a>Implementare il provider del gestore dei comandi di completamento
 Il provider del gestore del comando di completamento deriva da un oggetto , che rimane in ascolto di un evento di creazione della visualizzazione di testo e converte la vista da un oggetto , che consente l'aggiunta del comando alla catena di comandi della <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> shell Visual Studio, in un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Poiché questa classe è un'esportazione MEF, è anche possibile usarla per importare i servizi richiesti dal gestore comandi stesso.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Per implementare il provider del gestore dei comandi di completamento

1. Aggiungere un file denominato `TestCompletionCommandHandler` .

2. Aggiungere queste direttive using:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet11":::

3. Aggiungere una classe denominata `TestCompletionHandlerProvider` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Esportare questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> oggetto di "gestore di completamento token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "testo non crittografato" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> oggetto di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet12":::

4. Importare , che consente la conversione da a a , a e a che consente l'accesso ai <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> servizi Visual Studio <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> standard.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet13":::

5. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo per creare un'istanza del gestore dei comandi.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet14":::

## <a name="implement-the-completion-command-handler"></a>Implementare il gestore del comando di completamento
 Poiché il completamento dell'istruzione viene attivato da sequenze di tasti, è necessario implementare l'interfaccia per ricevere ed elaborare le sequenze di tasti che attivano, eserciteranno e chiuderanno <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la sessione di completamento.

#### <a name="to-implement-the-completion-command-handler"></a>Per implementare il gestore del comando di completamento

1. Aggiungere una classe denominata `TestCompletionCommandHandler` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet15":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet15":::

2. Aggiungere campi privati per il gestore comandi successivo (a cui si passa il comando), la visualizzazione di testo, il provider del gestore comandi (che consente l'accesso a vari servizi) e una sessione di completamento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet16":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet16":::

3. Aggiungere un costruttore che imposta la visualizzazione testo e i campi del provider e aggiunge il comando alla catena di comandi:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet17":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet17":::

4. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo passando il comando :

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet18":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet18":::

5. Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve una sequenza di tasti, deve eseguire una delle operazioni seguenti:

   - Consentire la scrittura del carattere nel buffer e quindi attivare o filtrare il completamento. A tale scopo, è necessario stampare i caratteri.

   - Eseguire il commit del completamento, ma non consentire la scrittura del carattere nel buffer. (Spazi vuoti, **TAB** e **INVIO** eseguire questa operazione quando viene visualizzata una sessione di completamento).

   - Consente di passare il comando al gestore successivo. (Tutti gli altri comandi).

     Poiché questo metodo può visualizzare l'interfaccia utente, chiamare per assicurarsi che non venga <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> chiamato in un contesto di automazione:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet19":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet19":::

6. Questo codice è un metodo privato che attiva la sessione di completamento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet20":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet20":::

7. L'esempio successivo è un metodo privato che annulla la sottoscrizione <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> dell'evento:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs" id="Snippet21":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb" id="Snippet21":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Per compilare e testare la soluzione CompletionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare un testo che includa la parola "add".

4. Quando si digita prima "a" e quindi "d", verrà visualizzato un elenco che contiene "addition" e "adaptation". Si noti che l'addizione è selezionata. Quando si digita un'altra "d", l'elenco deve contenere solo "addizione", che è ora selezionata. È possibile eseguire il commit dell'aggiunta premendo la BARRA SPAZIATRICE, **TAB** o **INVIO** oppure chiudendo l'elenco digitando ESC o qualsiasi altro tasto.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
