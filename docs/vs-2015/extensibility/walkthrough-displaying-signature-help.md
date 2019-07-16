---
title: 'Procedura dettagliata: Visualizzazione della Guida firma | Microsoft Docs'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202053"
---
# <a name="walkthrough-displaying-signature-help"></a>Procedura dettagliata: Visualizzazione della funzionalità di supporto alla firma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Supporto per la firma (detta anche *le informazioni sul parametro*) consente di visualizzare la firma di un metodo in una descrizione comando quando un utente digita il carattere iniziale dell'elenco parametri (in genere una parentesi di apertura). Com'è digitati un parametro e il separatore di parametro (in genere una virgola), la descrizione comando viene aggiornato per mostrare il parametro successivo in grassetto. È possibile definire supporto firma nel contesto di un servizio di linguaggio, è possibile definire il tipo di contenuto e l'estensione di nome file e visualizzare la Guida di firma per il solo tipo o è possibile visualizzare la Guida di firma per un tipo di contenuto esistente (ad esempio, "text"). Questa procedura dettagliata viene illustrato come visualizzare la Guida di firma per il tipo di contenuto "text".  
  
 Supporto per la firma viene in genere attivato digitando un carattere specifico, ad esempio, "(" (parentesi di apertura) e verrà eliminato digitando un altro carattere, ad esempio, ")" (la parentesi di chiusura). Funzionalità di IntelliSense che vengono attivate digitando un carattere può essere implementata usando un gestore di comandi per le sequenze di tasti (il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e un provider del gestore che implementa il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine supporto firma, ovvero l'elenco di firme che fanno parte di supporto firma, implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaccia e un provider di codice sorgente che implementa il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaccia. I provider sono parti componente Managed Extensibility Framework (MEF) e sono responsabili per le classi di origine e il controller di esportazione e importazione di servizi e Broker, ad esempio, il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente di passare nel buffer di testo e il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, che attiva la sessione di supporto firma.  
  
 Questa procedura dettagliata illustra come implementare supporto firma per un set di identificatori a livello di codice. In implementazioni complete, il linguaggio è responsabile di fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1. Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `SignatureHelpTest`.  
  
2. Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
4. Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** è impostata su `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementazione di firma consentono le firme e i parametri  
 L'origine supporto firma si basa sulle firme che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, ognuno dei quali contiene i parametri che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. In un'implementazione completa, sarebbe possibile ottenere queste informazioni nella documentazione di lingua, ma in questo esempio, le firme sono impostati come hardcoded.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Per implementare le firme di supporto firma e i parametri  
  
1. Aggiungere un file di classe e assegnargli il nome `SignatureHelpSource`.  
  
2. Aggiungere le istruzioni import seguenti.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Aggiungere una classe denominata `TestParameter` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Aggiungere un costruttore che imposta tutte le proprietà.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Aggiungere una classe denominata `TestSignature` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Aggiungere alcuni campi privati.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Aggiungere un costruttore che imposta i campi e sottoscrive il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente vengono inseriti in uno dei parametri nella firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> proprietà, in modo che venga generato il `CurrentParameterChanged` evento quando viene modificato il valore della proprietà.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Aggiungere un metodo che genera il `CurrentParameterChanged` evento.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole nella <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> al numero di virgole nella firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Aggiungere un gestore eventi per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento che chiama il `ComputeCurrentParameter()` (metodo).  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implementare gli altri parametri.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementazione dell'origine della Guida di firma  
 L'origine supporto firma è il set di firme per i quali è fornire informazioni.  
  
#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine supporto firma  
  
1. Aggiungere una classe denominata `TestSignatureHelpSource` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Aggiungere un riferimento al buffer di testo.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Aggiungere un costruttore che imposta il buffer di testo e il provider dell'origine supporto firma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono impostati come hardcoded, ma in un'implementazione completa si otterrebbe queste informazioni nella documentazione di linguaggio.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. Il metodo helper `CreateSignature()` viene fornito solo a scopo illustrativo.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio sono presenti solo due firme, ognuno dei quali include due parametri. Di conseguenza, questo metodo non è obbligatorio. In un'implementazione più completa, in cui più di un'origine supporto firma è disponibile, questo metodo viene utilizzato per stabilire se l'origine di supporto firma con priorità più alta possibile fornire una firma corrispondente. Se non è possibile, il metodo restituisce null e l'origine successiva priorità più elevata viene chiesto di fornire una corrispondenza.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Implementare il metodo Dispose ():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementazione del Provider di origine della Guida di firma  
 Il provider di origine supporto firma è responsabile per l'esportazione la parte di componente Managed Extensibility Framework (MEF) e per creare un'istanza di origine supporto firma.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine supporto firma  
  
1. Aggiungere una classe denominata `TestSignatureHelpSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di Before = "default".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando il `TestSignatureHelpSource`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementazione del gestore comando  
 Supporto per la firma viene in genere attivata da un (carattere e ignorato da un) caratteri. È possibile gestire tali pressioni di tasti implementando un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> in modo che attiva una sessione di supporto firma quando viene ricevuta una (carattere preceduto da un nome di metodo noto e chiude la sessione quando viene ricevuta una) caratteri.  
  
#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore del comando  
  
1. Aggiungere una classe denominata `TestSignatureHelpCommand` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Aggiungere campi privati per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adapter (che consente di aggiungere il gestore comando ai gestori di catena di comando), la visualizzazione di testo, il broker di supporto firma e sessione, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>e la successiva <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Aggiungere un costruttore per inizializzare i campi e per aggiungere il filtro di comando per la catena di filtri di comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per attivare la sessione di supporto firma quando riceve il filtro di comando un (carattere dopo uno dei nomi di metodo noto e per chiudere la sessione quando viene ricevuta una) carattere mentre è ancora attiva la sessione. In ogni caso, il comando viene inoltrato.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo in modo che venga sempre inoltra il comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementazione del Provider di comando di Help firma  
 È possibile fornire il comando Help firma, implementando la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per creare il gestore comando quando viene creata la visualizzazione di testo.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi supporto firma  
  
1. Aggiungere una classe denominata `TestSignatureHelpController` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ed esportarlo con la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Importa il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (usato per ottenere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto), il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usato per trovare la parola corrente) e il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (per attivare la sessione di supporto firma).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo creando il `TestSignatureCommandHandler`.  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest  
  
1. Compilare la soluzione.  
  
2. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3. Creare un file di testo e digitare un testo che include la parola "add" oltre a una parentesi di apertura.  
  
4. Dopo aver digitato la parentesi di apertura, si dovrebbe essere una descrizione comando che visualizza un elenco di due firme per i `add()` (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: collegamento di un tipo di contenuto a un'estensione](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
