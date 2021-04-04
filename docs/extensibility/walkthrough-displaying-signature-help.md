---
title: 'Procedura dettagliata: visualizzazione della Guida per le firme | Microsoft Docs'
description: Per informazioni su come visualizzare la guida per la firma per il tipo di contenuto testo, usare questa procedura dettagliata. La guida alla firma Visualizza la firma di un metodo in una descrizione comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6ffa2a0e646c11cb56d08ef91e3d7a4b9af7572
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217502"
---
# <a name="walkthrough-display-signature-help"></a>Procedura dettagliata: visualizzare la guida per la firma
La guida per la firma (nota anche come *informazioni sul parametro*) Visualizza la firma di un metodo in una descrizione comando quando un utente digita il carattere iniziale dell'elenco di parametri, in genere una parentesi di apertura. Poiché un parametro e un separatore di parametro (in genere una virgola) sono tipizzati, la descrizione comando viene aggiornata per visualizzare il parametro successivo in grassetto. È possibile definire la guida per la firma nei modi seguenti: nel contesto di un servizio di linguaggio, definire l'estensione del nome di file e il tipo di contenuto e visualizzare la guida della firma solo per quel tipo o visualizzare la guida della firma per un tipo di contenuto esistente (ad esempio, "testo"). In questa procedura dettagliata viene illustrato come visualizzare la guida per la firma per il tipo di contenuto "Text".

 La guida alla firma viene in genere attivata digitando un carattere specifico, ad esempio, "(" (parentesi di apertura) e chiuso digitando un altro carattere, ad esempio, ")" (parentesi di chiusura). Le funzionalità di IntelliSense attivate digitando un carattere possono essere implementate tramite un gestore di comandi per le sequenze di tasti ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia) e un provider del gestore che implementa l' <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine della Guida di firma, ovvero l'elenco di firme che partecipano alla guida alla firma, implementare l' <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaccia e un provider di origine che esegue l' <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaccia. I provider sono parti Managed Extensibility Framework (MEF) componenti e sono responsabili dell'esportazione delle classi di origine e del controller e dell'importazione di servizi e broker, ad esempio, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , che consente di spostarsi nel buffer di testo e, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> che attiva la sessione di supporto della firma.

 In questa procedura dettagliata viene illustrato come impostare la guida della firma per un set di identificatori hardcoded. Nelle implementazioni complete il linguaggio è responsabile della fornitura di tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `SignatureHelpTest` .

2. Aggiungere un modello di elemento classificatore editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

4. Aggiungere i riferimenti seguenti al progetto e verificare che **CopyLocal** sia impostato su `false` :

     Microsoft. VisualStudio. Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft. VisualStudio. OLE. Interop

     Microsoft. VisualStudio. Shell. 14.0

     Microsoft. VisualStudio. TextManager. Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementa firme e parametri della Guida di firma
 L'origine della Guida di firma è basata sulle firme che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , ognuna delle quali contiene parametri che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . In un'implementazione completa queste informazioni vengono ottenute dalla documentazione della lingua, ma in questo esempio le firme sono hardcoded.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Per implementare le firme e i parametri della Guida di firma

1. Aggiungere un file di classe e assegnargli il nome `SignatureHelpSource`.

2. Aggiungere le importazioni seguenti.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet1":::

3. Aggiungere una classe denominata `TestParameter` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet2":::

4. Aggiungere un costruttore che imposta tutte le proprietà.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet3":::

5. Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet4":::

6. Aggiungere una classe denominata `TestSignature` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet5":::

7. Aggiungere alcuni campi privati.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet6":::

8. Aggiungere un costruttore che imposta i campi e sottoscrive l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet7":::

9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente compila uno dei parametri nella firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet8":::

10. Implementare la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Proprietà in modo che generi l' `CurrentParameterChanged` evento quando viene modificato il valore della proprietà.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet9":::

11. Aggiungere un metodo che genera l' `CurrentParameterChanged` evento.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet10":::

12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole nell'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> con il numero di virgole nella firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet11":::

13. Aggiungere un gestore eventi per l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento che chiama il `ComputeCurrentParameter()` metodo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet12":::

14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà include un oggetto <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet13":::

15. Implementare gli altri parametri.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet14":::

## <a name="implement-the-signature-help-source"></a>Implementare l'origine della Guida di firma
 L'origine della Guida di firma è il set di firme per cui si forniscono le informazioni.

#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine della Guida di firma

1. Aggiungere una classe denominata `TestSignatureHelpSource` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet15":::

2. Aggiungere un riferimento al buffer di testo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet16":::

3. Aggiungere un costruttore che imposta il buffer di testo e il provider di origine della Guida di firma.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet17":::

4. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono hardcoded, ma in un'implementazione completa si ottengono queste informazioni dalla documentazione della lingua.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet18":::

5. Il metodo helper `CreateSignature()` viene fornito solo per l'illustrazione.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet19":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet19":::

6. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio sono disponibili solo due firme, ognuna delle quali ha due parametri. Pertanto, questo metodo non è obbligatorio. In un'implementazione più completa, in cui sono disponibili più origini della Guida per la firma, questo metodo viene utilizzato per decidere se l'origine della guida della firma con la priorità più alta può fornire una firma corrispondente. In caso contrario, il metodo restituisce null e all'origine con priorità più alta successiva viene richiesto di fornire una corrispondenza.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet20":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet20":::

7. Implementare il `Dispose()` Metodo:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet21":::

## <a name="implement-the-signature-help-source-provider"></a>Implementare il provider di origine della Guida di firma
 Il provider di origine della Guida di firma è responsabile dell'esportazione della parte del componente Managed Extensibility Framework (MEF) e della creazione di un'istanza dell'origine della Guida di firma.

#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine della Guida alla firma

1. Aggiungere una classe denominata `TestSignatureHelpSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> ed esportarla con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text" e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di before = "default".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet22":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet22":::

2. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando un'istanza di `TestSignatureHelpSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet23":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet23":::

## <a name="implement-the-command-handler"></a>Implementare il gestore di comandi
 La guida alla firma viene in genere attivata da una parentesi di apertura "(" carattere e chiusa da un carattere parentesi di chiusura ")". È possibile gestire queste sequenze di tasti eseguendo un oggetto in <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> modo che venga attivata una sessione di supporto della firma quando riceve un carattere di parentesi di apertura preceduto da un nome di metodo noto e chiude la sessione quando riceve un carattere di parentesi di chiusura.

#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore di comandi

1. Aggiungere una classe denominata `TestSignatureHelpCommand` che implementi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet24":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet24":::

2. Aggiungere campi privati per la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> scheda (che consente di aggiungere il gestore del comando alla catena di gestori di comandi), la visualizzazione di testo, la firma e la sessione di supporto della firma, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> e il successivo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet25":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet25":::

3. Aggiungere un costruttore per inizializzare questi campi e aggiungere il filtro del comando alla catena di filtri dei comandi.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet26":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet26":::

4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per attivare la sessione di supporto della firma quando il filtro del comando riceve una parentesi di apertura "(" dopo uno dei nomi di metodo noti e per chiudere la sessione quando riceve un carattere parentesi di chiusura ")" mentre la sessione è ancora attiva. In ogni caso, il comando viene inviato.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet27":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet27":::

5. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo in modo che inoltri sempre il comando.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet28":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet28":::

## <a name="implement-the-signature-help-command-provider"></a>Implementare il provider di comandi della Guida per la firma
 È possibile specificare il comando firma Guida implementando l'oggetto <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per creare un'istanza del gestore di comando quando viene creata la visualizzazione di testo.

### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi della Guida per la firma

1. Aggiungere una classe denominata `TestSignatureHelpController` che implementi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ed esporti l'oggetto con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet29":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet29":::

2. Importare l' <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> oggetto (usato per ottenere <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , dato l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usato per trovare la parola corrente) e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (per attivare la sessione della Guida di firma).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet30":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet30":::

3. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Metodo creando un'istanza di `TestSignatureCommandHandler` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb" id="Snippet31":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs" id="Snippet31":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include la parola "Add" più una parentesi di apertura.

4. Dopo aver digitato la parentesi di apertura, viene visualizzata una descrizione comando che visualizza un elenco delle due firme per il `add()` metodo.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
