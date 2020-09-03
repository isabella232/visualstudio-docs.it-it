---
title: 'Procedura dettagliata: visualizzazione della Guida per le firme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b88c8555904bb31c2804579459ad3096d640b0c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904810"
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

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Aggiungere una classe denominata `TestParameter` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Aggiungere un costruttore che imposta tutte le proprietà.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Aggiungere una classe denominata `TestSignature` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Aggiungere alcuni campi privati.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Aggiungere un costruttore che imposta i campi e sottoscrive l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente compila uno dei parametri nella firma.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementare la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Proprietà in modo che generi l' `CurrentParameterChanged` evento quando viene modificato il valore della proprietà.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Aggiungere un metodo che genera l' `CurrentParameterChanged` evento.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole nell'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> con il numero di virgole nella firma.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Aggiungere un gestore eventi per l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento che chiama il `ComputeCurrentParameter()` metodo.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà include un oggetto <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementare gli altri parametri.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementare l'origine della Guida di firma
 L'origine della Guida di firma è il set di firme per cui si forniscono le informazioni.

#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine della Guida di firma

1. Aggiungere una classe denominata `TestSignatureHelpSource` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Aggiungere un riferimento al buffer di testo.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Aggiungere un costruttore che imposta il buffer di testo e il provider di origine della Guida di firma.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono hardcoded, ma in un'implementazione completa si ottengono queste informazioni dalla documentazione della lingua.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Il metodo helper `CreateSignature()` viene fornito solo per l'illustrazione.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio sono disponibili solo due firme, ognuna delle quali ha due parametri. Pertanto, questo metodo non è obbligatorio. In un'implementazione più completa, in cui sono disponibili più origini della Guida per la firma, questo metodo viene utilizzato per decidere se l'origine della guida della firma con la priorità più alta può fornire una firma corrispondente. In caso contrario, il metodo restituisce null e all'origine con priorità più alta successiva viene richiesto di fornire una corrispondenza.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementare il `Dispose()` Metodo:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementare il provider di origine della Guida di firma
 Il provider di origine della Guida di firma è responsabile dell'esportazione della parte del componente Managed Extensibility Framework (MEF) e della creazione di un'istanza dell'origine della Guida di firma.

#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine della Guida alla firma

1. Aggiungere una classe denominata `TestSignatureHelpSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> ed esportarla con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text" e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di before = "default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando un'istanza di `TestSignatureHelpSource` .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementare il gestore di comandi
 La guida alla firma viene in genere attivata da una parentesi di apertura "(" carattere e chiusa da un carattere parentesi di chiusura ")". È possibile gestire queste sequenze di tasti eseguendo un oggetto in <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> modo che venga attivata una sessione di supporto della firma quando riceve un carattere di parentesi di apertura preceduto da un nome di metodo noto e chiude la sessione quando riceve un carattere di parentesi di chiusura.

#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore di comandi

1. Aggiungere una classe denominata `TestSignatureHelpCommand` che implementi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Aggiungere campi privati per la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> scheda (che consente di aggiungere il gestore del comando alla catena di gestori di comandi), la visualizzazione di testo, la firma e la sessione di supporto della firma, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> e il successivo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Aggiungere un costruttore per inizializzare questi campi e aggiungere il filtro del comando alla catena di filtri dei comandi.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per attivare la sessione di supporto della firma quando il filtro del comando riceve una parentesi di apertura "(" dopo uno dei nomi di metodo noti e per chiudere la sessione quando riceve un carattere parentesi di chiusura ")" mentre la sessione è ancora attiva. In ogni caso, il comando viene inviato.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo in modo che inoltri sempre il comando.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementare il provider di comandi della Guida per la firma
 È possibile specificare il comando firma Guida implementando l'oggetto <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per creare un'istanza del gestore di comando quando viene creata la visualizzazione di testo.

### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi della Guida per la firma

1. Aggiungere una classe denominata `TestSignatureHelpController` che implementi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ed esporti l'oggetto con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importare l' <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> oggetto (usato per ottenere <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , dato l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usato per trovare la parola corrente) e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (per attivare la sessione della Guida di firma).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Metodo creando un'istanza di `TestSignatureCommandHandler` .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include la parola "Add" più una parentesi di apertura.

4. Dopo aver digitato la parentesi di apertura, viene visualizzata una descrizione comando che visualizza un elenco delle due firme per il `add()` metodo.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
