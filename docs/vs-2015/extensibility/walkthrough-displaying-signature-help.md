---
title: 'Procedura dettagliata: visualizzazione della Guida per le firme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202053"
---
# <a name="walkthrough-displaying-signature-help"></a>Procedura dettagliata: visualizzazione della Guida per la firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La guida per la firma (nota anche come *informazioni sul parametro*) Visualizza la firma di un metodo in una descrizione comando quando un utente digita il carattere iniziale dell'elenco di parametri, in genere una parentesi di apertura. Poiché un parametro e un separatore di parametro (in genere una virgola) sono tipizzati, la descrizione comando viene aggiornata per visualizzare il parametro successivo in grassetto. È possibile definire la guida per la firma nel contesto di un servizio di linguaggio oppure è possibile definire l'estensione del nome di file e il tipo di contenuto e visualizzare la guida della firma solo per quel tipo oppure è possibile visualizzare la guida della firma per un tipo di contenuto esistente (ad esempio, "Text"). In questa procedura dettagliata viene illustrato come visualizzare la guida per la firma per il tipo di contenuto "Text".  
  
 La guida alla firma viene in genere attivata digitando un carattere specifico, ad esempio, "(" (parentesi di apertura) e chiuso digitando un altro carattere, ad esempio, ")" (parentesi di chiusura). Le funzionalità di IntelliSense attivate digitando un carattere possono essere implementate tramite un gestore di comandi per le sequenze di tasti ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia) e un provider del gestore che implementa l' <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine della Guida di firma, ovvero l'elenco di firme che partecipano alla guida alla firma, implementare l' <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaccia e un provider di origine che implementi l' <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaccia. I provider sono parti Managed Extensibility Framework (MEF) componenti e sono responsabili dell'esportazione delle classi di origine e del controller e dell'importazione di servizi e broker, ad esempio, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , che consente di spostarsi nel buffer di testo e, <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> che attiva la sessione di supporto della firma.  
  
 In questa procedura dettagliata viene illustrato come implementare la guida della firma per un set di identificatori hardcoded. Nelle implementazioni complete il linguaggio è responsabile della fornitura di tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `SignatureHelpTest` .  
  
2. Aggiungere un modello di elemento classificatore editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
4. Aggiungere i riferimenti seguenti al progetto e verificare che **CopyLocal** sia impostato su `false` :  
  
     Microsoft. VisualStudio. Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. TextManager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementazione delle firme e dei parametri della Guida di firma  
 L'origine della Guida di firma è basata sulle firme che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , ognuna delle quali contiene parametri che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . In un'implementazione completa queste informazioni vengono ottenute dalla documentazione della lingua, ma in questo esempio le firme sono hardcoded.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Per implementare le firme e i parametri della Guida di firma  
  
1. Aggiungere un file di classe e assegnargli il nome `SignatureHelpSource`.  
  
2. Aggiungere le importazioni seguenti.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Aggiungere una classe denominata `TestParameter` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Aggiungere un costruttore che imposta tutte le proprietà.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Aggiungere una classe denominata `TestSignature` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Aggiungere alcuni campi privati.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Aggiungere un costruttore che imposta i campi e sottoscrive l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente compila uno dei parametri nella firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementare la <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> Proprietà in modo che generi l' `CurrentParameterChanged` evento quando viene modificato il valore della proprietà.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Aggiungere un metodo che genera l' `CurrentParameterChanged` evento.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole nell'oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> con il numero di virgole nella firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Aggiungere un gestore eventi per l' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento che chiama il `ComputeCurrentParameter()` metodo.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà include un oggetto <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementare gli altri parametri.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementazione dell'origine della Guida di firma  
 L'origine della Guida di firma è il set di firme per cui si forniscono le informazioni.  
  
#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine della Guida di firma  
  
1. Aggiungere una classe denominata `TestSignatureHelpSource` che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Aggiungere un riferimento al buffer di testo.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Aggiungere un costruttore che imposta il buffer di testo e il provider di origine della Guida di firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono hardcoded, ma in un'implementazione completa si ottengono queste informazioni dalla documentazione della lingua.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Il metodo helper `CreateSignature()` viene fornito solo per l'illustrazione.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio sono disponibili solo due firme, ognuna delle quali ha due parametri. Pertanto, questo metodo non è obbligatorio. In un'implementazione più completa, in cui sono disponibili più origini della Guida per la firma, questo metodo viene utilizzato per decidere se l'origine della guida della firma con la priorità più alta può fornire una firma corrispondente. In caso contrario, il metodo restituisce null e all'origine con priorità più alta successiva viene richiesto di fornire una corrispondenza.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Implementare il metodo Dispose ():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementazione del provider di origine della Guida di firma  
 Il provider di origine della Guida di firma è responsabile dell'esportazione della parte del componente Managed Extensibility Framework (MEF) e della creazione di un'istanza dell'origine della Guida di firma.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine della Guida alla firma  
  
1. Aggiungere una classe denominata `TestSignatureHelpSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> ed esportarla con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text" e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di before = "default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando un'istanza di `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementazione del gestore dei comandi  
 La guida per la firma viene in genere attivata da un carattere (carattere ed eliminato da un). È possibile gestire queste sequenze di tasti implementando un oggetto in <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> modo che venga attivata una sessione di supporto della firma quando riceve un oggetto (carattere preceduto da un nome di metodo noto e la sessione viene rilasciata quando riceve un carattere).  
  
#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore di comandi  
  
1. Aggiungere una classe denominata `TestSignatureHelpCommand` che implementi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Aggiungere campi privati per la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> scheda (che consente di aggiungere il gestore del comando alla catena di gestori di comandi), la visualizzazione di testo, la firma e la sessione di supporto della firma, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> e il successivo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Aggiungere un costruttore per inizializzare questi campi e aggiungere il filtro del comando alla catena di filtri dei comandi.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per attivare la sessione di supporto della firma quando il filtro del comando riceve un carattere (dopo uno dei nomi di metodo noti e per ignorare la sessione quando riceve un) quando la sessione è ancora attiva. In ogni caso, il comando viene inviato.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo in modo che inoltri sempre il comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementazione del provider di comandi della Guida per la firma  
 È possibile specificare il comando firma Guida implementando l'oggetto <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per creare un'istanza del gestore di comando quando viene creata la visualizzazione di testo.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi della Guida per la firma  
  
1. Aggiungere una classe denominata `TestSignatureHelpController` che implementi <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ed esporti l'oggetto con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Importare l' <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> oggetto (usato per ottenere <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , dato l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usato per trovare la parola corrente) e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (per attivare la sessione della Guida di firma).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> Metodo creando un'istanza di `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirla nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest  
  
1. Compilare la soluzione.  
  
2. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3. Creare un file di testo e digitare il testo che include la parola "Add" più una parentesi di apertura.  
  
4. Dopo aver digitato la parentesi di apertura, viene visualizzata una descrizione comando che visualizza un elenco delle due firme per il `add()` metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
