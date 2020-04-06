---
title: 'Procedura dettagliata: Visualizzazione della Guida per la firma . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697425"
---
# <a name="walkthrough-display-signature-help"></a>Procedura dettagliata: Visualizza guida firmaWalkthrough: Display Signature Help
La Guida alla firma (nota anche come *informazioni sui*parametri ) visualizza la firma di un metodo in una descrizione comando quando un utente digita il carattere iniziale dell'elenco di parametri (in genere una parentesi di apertura). Quando vengono digitati un parametro e un separatore di parametro (in genere una virgola), la descrizione comando viene aggiornata per mostrare il parametro successivo in grassetto. È possibile definire la Guida per la firma nei modi seguenti: nel contesto di un servizio di linguaggio, definire l'estensione del nome file e il tipo di contenuto e visualizzare la Guida per la firma solo per quel tipo oppure visualizzare la Guida per la firma per un tipo di contenuto esistente (ad esempio, "testo"). In questa procedura dettagliata viene illustrato come visualizzare la Guida per la firma per il tipo di contenuto "testo".

 La Guida per la firma viene in genere attivata digitando un carattere specifico, ad esempio "(" (parentesi di apertura) e chiusa digitando un altro carattere, ad esempio ")" (parentesi di chiusura). Le funzionalità Di IntelliSense che vengono attivate digitando un carattere possono essere <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementate utilizzando un gestore di comando per le sequenze di tasti (l'interfaccia) e un provider di gestori che implementa l'interfaccia. <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Per creare l'origine della Guida per la firma, ovvero <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> l'elenco delle firme <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> che fanno parte della Guida per la firma, implementare l'interfaccia e un provider di origine che esegue l'interfaccia. I provider sono parti del componente Managed Extensibility Framework (MEF) e sono responsabili dell'esportazione delle <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>classi di origine e controller e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>dell'importazione di servizi e broker, ad esempio , che consente di spostarsi nel buffer di testo e di , che attiva la sessione della Guida per la firma.

 In questa procedura dettagliata viene illustrato come impostare la Guida della firma per un set di identificatori hardcoded. Nelle implementazioni complete, il linguaggio è responsabile della fornitura di tale contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `SignatureHelpTest`la soluzione .

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

4. Aggiungere i riferimenti seguenti al progetto e assicurarsi `false`che **CopyLocal** sia impostato su :

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementare le firme e i parametri della Guida per la firma
 L'origine della Guida per <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>la firma si basa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>sulle firme che implementano , ognuna delle quali contiene parametri che implementano . In un'implementazione completa, queste informazioni sono ottenute dalla documentazione del linguaggio, ma in questo esempio, le firme sono hardcoded.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Per implementare le firme e i parametri della Guida per le firme di firma

1. Aggiungere un file di classe e assegnargli il nome `SignatureHelpSource`.

2. Aggiungere le importazioni seguenti.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Aggiungere una `TestParameter` classe <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>denominata che implementa .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Aggiungere un costruttore che imposta tutte le proprietà.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Aggiungere le <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>proprietà di .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Aggiungere una `TestSignature` classe <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>denominata che implementa .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Aggiungere alcuni campi privati.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Aggiungere un costruttore che imposta i <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> campi e sottoscrive l'evento.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Dichiarare `CurrentParameterChanged` un evento. Questo evento viene generato quando l'utente compila uno dei parametri nella firma.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> la proprietà in `CurrentParameterChanged` modo che generi l'evento quando il valore della proprietà viene modificato.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Aggiungere un metodo `CurrentParameterChanged` che genera l'evento.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Aggiungere un metodo che calcola il parametro corrente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> confrontando il numero di virgole nel file con il numero di virgole nella firma.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Aggiungere un gestore <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventi per `ComputeCurrentParameter()` l'evento che chiama il metodo.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà <xref:Microsoft.VisualStudio.Text.ITrackingSpan> contiene un che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implementare gli altri parametri.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementare l'origine della Guida per la firma
 L'origine della Guida per la firma è l'insieme di firme per cui si forniscono informazioni.

#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine della Guida per la firma

1. Aggiungere una `TestSignatureHelpSource` classe <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>denominata che implementa .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Aggiungere un riferimento al buffer di testo.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Aggiungere un costruttore che imposta il buffer di testo e il provider di origine della Guida per la firma.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono hardcoded, ma in un'implementazione completa si otterrebbero queste informazioni dalla documentazione del linguaggio.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. Il metodo `CreateSignature()` helper viene fornito solo a scopo illustrativo.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio, ci sono solo due firme, ognuna delle quali ha due parametri. Pertanto, questo metodo non è necessario. In un'implementazione più completa, in cui sono disponibili più origini della Guida per la firma, questo metodo viene utilizzato per decidere se l'origine della Guida per la firma con la priorità più alta può fornire una firma corrispondente. In caso contrario, il metodo restituisce null e all'origine con priorità più alta successiva viene richiesto di fornire una corrispondenza.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementare `Dispose()` il metodo:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementare il provider di origine della Guida per la firma
 Il provider di origine della Guida per la firma è responsabile dell'esportazione della parte del componente Managed Extensibility Framework (MEF) e della creazione di un'istanza dell'origine della Guida per la firma.

#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine della Guida per la firma

1. Aggiungere una `TestSignatureHelpSourceProvider` classe <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>denominata che implementa <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ed esportarla con <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> un , a di "text" e un di Before , "default".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementare mediante <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> la `TestSignatureHelpSource`creazione di un'istanza di .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementare il gestore comandi
 La Guida della firma viene in genere attivata da una parentesi di apertura "(" carattere e chiusa da una parentesi di chiusura ")". È possibile gestire queste sequenze <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> di tasti eseguendo un modo in modo che attivi una sessione della Guida per la firma quando riceve un carattere di parentesi di apertura preceduto da un nome di metodo noto e chiude la sessione quando riceve un carattere di parentesi di chiusura.

#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore comandi

1. Aggiungere una `TestSignatureHelpCommand` classe <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>denominata che implementa .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Aggiungere campi privati <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per l'adapter (che consente di aggiungere il gestore comandi alla catena di <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>gestori di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>comandi), la visualizzazione di testo, il broker e la sessione della Guida per la firma, un , e il successivo .

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Aggiungere un costruttore per inizializzare questi campi e aggiungere il filtro di comando alla catena di filtri di comando.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> il metodo per attivare la sessione della Guida per la firma quando il filtro di comando riceve una parentesi di apertura "(" dopo uno dei nomi di metodo noti e per chiudere la sessione quando riceve una parentesi di chiusura ")" mentre la sessione è ancora attiva. In ogni caso, il comando viene inoltrato.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo in modo che inoltri sempre il comando.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementare il provider di comandi della Guida per la firma
 È possibile fornire il comando <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> Guida per la firma implementando l'oggetto per creare un'istanza del gestore comandi quando viene creata la visualizzazione di testo.

### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi della Guida per le firme

1. Aggiungere una `TestSignatureHelpController` classe <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> denominata che <xref:Microsoft.VisualStudio.Utilities.NameAttribute>implementa <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>ed <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>esportata con i dati , , e .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importare <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> il (utilizzato <xref:Microsoft.VisualStudio.Text.Editor.ITextView>per ottenere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> l'oggetto , dato l'oggetto), l'oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (utilizzato per trovare la parola corrente) e il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (per attivare la sessione della Guida per la firma).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementare <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> il metodo mediante `TestSignatureCommandHandler`la creazione di un'istanza di .

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and Test the Code
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare del testo che includa la parola "add" più una parentesi di apertura.

4. Dopo aver digitato la parentesi di apertura, verrà visualizzata una `add()` descrizione comando che visualizza un elenco delle due firme per il metodo.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
