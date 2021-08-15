---
title: 'Procedura dettagliata: Visualizzazione della Guida per la firma | Microsoft Docs'
description: Informazioni su come visualizzare la Guida per la firma per il tipo di contenuto di testo usando questa procedura dettagliata. La Guida alla firma visualizza la firma di un metodo in una descrizione comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d4c8e69c261b25a4f3a425fc11eb8ccd259dbad2bf951f980e985163a23b4d0d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374624"
---
# <a name="walkthrough-display-signature-help"></a>Procedura dettagliata: Visualizzare la Guida per la firma
La Guida alla firma (nota anche come *Informazioni* sui parametri ) visualizza la firma di un metodo in una descrizione comando quando un utente specifica il carattere iniziale dell'elenco di parametri (in genere una parentesi di apertura). Quando vengono digitati un parametro e un separatore di parametri (in genere una virgola), la descrizione comando viene aggiornata per visualizzare il parametro successivo in grassetto. È possibile definire la Guida per la firma nei modi seguenti: nel contesto di un servizio di linguaggio, definire l'estensione e il tipo di contenuto del nome file e visualizzare la Guida per la firma solo per quel tipo oppure visualizzare la Guida per la firma per un tipo di contenuto esistente, ad esempio "text". Questa procedura dettagliata illustra come visualizzare la Guida per la firma per il tipo di contenuto "text".

 La Guida alla firma viene in genere attivata digitando un carattere specifico, ad esempio "(" (parentesi di apertura) e ignorato digitando un altro carattere, ad esempio ")" (parentesi di chiusura). Le funzionalità di IntelliSense attivate dalla digitazione di un carattere possono essere implementate usando un gestore di comandi per le sequenze di tasti (l'interfaccia ) e un provider di gestori che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> l'interfaccia . Per creare l'origine della Guida per la firma, ovvero l'elenco delle firme che fanno parte della Guida per la firma, implementare l'interfaccia e un provider di origine <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> che esegue <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> l'interfaccia. I provider sono parti Managed Extensibility Framework (MEF) e sono responsabili dell'esportazione delle classi di origine e controller e dell'importazione di servizi e broker, ad esempio , che consente di spostarsi nel buffer di testo e di , che attiva la sessione della Guida per la <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> firma.

 Questa procedura dettagliata illustra come configurare la Guida per la firma per un set hard-coded di identificatori. Nelle implementazioni complete, il linguaggio è responsabile di fornire tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Nuovo Project** selezionare Visual **C# /Extensibility** e quindi **VSIX Project**. Assegnare alla soluzione il nome `SignatureHelpTest` .

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

4. Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** sia impostato su `false` :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementare firme e parametri della Guida per la firma
 L'origine della Guida alla firma si basa sulle firme che implementano , ognuna delle quali <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> contiene parametri che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . In un'implementazione completa, queste informazioni vengono ottenute dalla documentazione del linguaggio, ma in questo esempio le firme sono hard-coded.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Per implementare le firme e i parametri della Guida per la firma

1. Aggiungere un file di classe e assegnargli il nome `SignatureHelpSource`.

2. Aggiungere le importazioni seguenti.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet1":::

3. Aggiungere una classe denominata `TestParameter` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet2":::

4. Aggiungere un costruttore che imposta tutte le proprietà.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet3":::

5. Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet4":::

6. Aggiungere una classe denominata `TestSignature` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet5":::

7. Aggiungere alcuni campi privati.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet6":::

8. Aggiungere un costruttore che imposta i campi e sottoscrive <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> l'evento .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet7":::

9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente compila uno dei parametri nella firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet8":::

10. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> la proprietà in modo che genera l'evento quando il valore della proprietà viene `CurrentParameterChanged` modificato.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet9":::

11. Aggiungere un metodo che genera `CurrentParameterChanged` l'evento .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet10":::

12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole in con il numero di <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> virgole nella firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet11":::

13. Aggiungere un gestore eventi per <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> l'evento che chiama il metodo `ComputeCurrentParameter()` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet12":::

14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> oggetto che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet13":::

15. Implementare gli altri parametri.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet14":::

## <a name="implement-the-signature-help-source"></a>Implementare l'origine della Guida per la firma
 L'origine della Guida per la firma è il set di firme per cui si forniscono informazioni.

#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine della Guida per la firma

1. Aggiungere una classe denominata `TestSignatureHelpSource` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet15":::

2. Aggiungere un riferimento al buffer di testo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet16":::

3. Aggiungere un costruttore che imposta il buffer di testo e il provider di origine della Guida per la firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet17":::

4. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio le firme sono hard coded, ma in un'implementazione completa si ottengono queste informazioni dalla documentazione del linguaggio.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet18":::

5. Il metodo helper `CreateSignature()` viene fornito solo a scopo illustrativo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet19":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet19":::

6. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio sono presenti solo due firme, ognuna delle quali ha due parametri. Pertanto, questo metodo non è obbligatorio. In un'implementazione più completa, in cui sono disponibili più origini della Guida per la firma, questo metodo viene usato per decidere se l'origine della Guida per la firma con la priorità più alta può fornire una firma corrispondente. In caso contrario, il metodo restituisce Null e all'origine con priorità successiva viene richiesto di specificare una corrispondenza.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet20":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet20":::

7. Implementare il `Dispose()` metodo :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet21":::

## <a name="implement-the-signature-help-source-provider"></a>Implementare il provider di origine della Guida per la firma
 Il provider di origine della Guida alla firma è responsabile dell'esportazione della parte Managed Extensibility Framework (MEF) e della creazione di un'istanza dell'origine della Guida per la firma.

#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine della Guida per la firma

1. Aggiungere una classe denominata che implementa e esportarla con , un di "text" e un `TestSignatureHelpSourceProvider` <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> elemento <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> before="default".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet22":::

2. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando un'istanza di `TestSignatureHelpSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet23":::

## <a name="implement-the-command-handler"></a>Implementare il gestore dei comandi
 La Guida alla firma viene in genere attivata da una parentesi di apertura "(" carattere e ignorata da una parentesi di chiusura ")". È possibile gestire queste sequenze di tasti eseguendo un in modo che attiva una sessione della Guida alla firma quando riceve un carattere parentesi di apertura preceduto da un nome di metodo noto e chiude la sessione quando riceve un carattere parentesi di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chiusura.

#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore dei comandi

1. Aggiungere una classe denominata `TestSignatureHelpCommand` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet24":::

2. Aggiungere campi privati per l'adapter (che consente di aggiungere il gestore comandi alla catena di gestori di comandi), la visualizzazione di testo, il broker e la sessione della Guida per la firma, un e il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> successivo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet25":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet25":::

3. Aggiungere un costruttore per inizializzare questi campi e aggiungere il filtro di comando alla catena di filtri di comando.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet26":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet26":::

4. Implementare il metodo per attivare la sessione della Guida per la firma quando il filtro di comando riceve una parentesi di apertura "(" carattere dopo uno dei nomi di metodo noti e per chiudere la sessione quando riceve una parentesi di chiusura ")" mentre la sessione è ancora <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> attiva. In ogni caso, il comando viene inoltrato.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet27":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet27":::

5. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo in modo da inoltrare sempre il comando.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet28":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet28":::

## <a name="implement-the-signature-help-command-provider"></a>Implementare il provider di comandi della Guida per la firma
 È possibile fornire il comando Signature Help implementando per creare un'istanza del gestore dei comandi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> quando viene creata la visualizzazione testo.

### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi della Guida per la firma

1. Aggiungere una classe denominata che implementa ed esporta la classe `TestSignatureHelpController` <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> con , e <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet29":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet29":::

2. Importare (usato per ottenere l'oggetto , dato l'oggetto ), (usato per trovare la parola corrente) e (per attivare <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> la sessione della Guida per la <xref:Microsoft.VisualStudio.Text.Editor.ITextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> firma).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet30":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet30":::

3. Implementare <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> il metodo creando un'istanza di `TestSignatureCommandHandler` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet31":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet31":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include la parola "add" più una parentesi di apertura.

4. Dopo aver digitato la parentesi di apertura, verrà visualizzata una descrizione comando che visualizza un elenco delle due firme per il `add()` metodo.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
