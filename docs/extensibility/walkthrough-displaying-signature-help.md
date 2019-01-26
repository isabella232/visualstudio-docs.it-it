---
title: 'Procedura dettagliata: Visualizzazione della Guida firma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5923efe859f6fe04468e6659d8df46b8b3d2a1cd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981129"
---
# <a name="walkthrough-display-signature-help"></a>Procedura dettagliata: Visualizzare la Guida di firma
Supporto per la firma (detta anche *le informazioni sul parametro*) consente di visualizzare la firma di un metodo in una descrizione comando quando un utente digita il carattere iniziale dell'elenco parametri (in genere una parentesi di apertura). Com'è digitati un parametro e il separatore di parametro (in genere una virgola), la descrizione comando viene aggiornato per mostrare il parametro successivo in grassetto. È possibile definire supporto firma nei modi seguenti: nel contesto di un servizio di linguaggio, definire il proprio estensione di file e il tipo di contenuto e visualizzare la Guida di firma per il solo tipo o visualizzare la Guida di firma per un tipo di contenuto esistente (ad esempio, "text"). Questa procedura dettagliata viene illustrato come visualizzare la Guida di firma per il tipo di contenuto "text".  
  
 Supporto per la firma viene in genere attivato digitando un carattere specifico, ad esempio, "(" (parentesi di apertura) e verrà eliminato digitando un altro carattere, ad esempio, ")" (la parentesi di chiusura). Funzionalità di IntelliSense che vengono attivate digitando un carattere può essere implementata usando un gestore di comandi per le sequenze di tasti (il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e un provider del gestore che implementa il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine supporto firma, ovvero l'elenco di firme che fanno parte di supporto firma, implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaccia e un provider di origine che esegue il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaccia. I provider sono parti componente Managed Extensibility Framework (MEF) e sono responsabili per le classi di origine e il controller di esportazione e importazione di servizi e Broker, ad esempio, il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente di passare nel buffer di testo e il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, che attiva la sessione di supporto firma.  
  
 Questa procedura dettagliata illustra come configurare supporto firma per un set di identificatori a livello di codice. In implementazioni complete, il linguaggio è responsabile di fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `SignatureHelpTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** è impostata su `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implement-signature-help-signatures-and-parameters"></a>Implementare firme di supporto firma e i parametri  
 L'origine supporto firma si basa sulle firme che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, ognuno dei quali contiene i parametri che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. In un'implementazione completa, sarebbe possibile ottenere queste informazioni nella documentazione di lingua, ma in questo esempio, le firme sono impostati come hardcoded.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Per implementare le firme di supporto firma e i parametri  
  
1.  Aggiungere un file di classe e assegnargli il nome `SignatureHelpSource`.  
  
2.  Aggiungere le istruzioni import seguenti.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Aggiungere una classe denominata `TestParameter` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Aggiungere un costruttore che imposta tutte le proprietà.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Aggiungere una classe denominata `TestSignature` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Aggiungere alcuni campi privati.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Aggiungere un costruttore che imposta i campi e sottoscrive il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente vengono inseriti in uno dei parametri nella firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> proprietà, in modo che venga generato il `CurrentParameterChanged` evento quando viene modificato il valore della proprietà.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Aggiungere un metodo che genera il `CurrentParameterChanged` evento.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole nella <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> al numero di virgole nella firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Aggiungere un gestore eventi per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento che chiama il `ComputeCurrentParameter()` (metodo).  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implementare gli altri parametri.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## <a name="implement-the-signature-help-source"></a>Implementare l'origine supporto firma  
 L'origine supporto firma è il set di firme per i quali è fornire informazioni.  
  
#### <a name="to-implement-the-signature-help-source"></a>Per implementare l'origine supporto firma  
  
1.  Aggiungere una classe denominata `TestSignatureHelpSource` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Aggiungere un riferimento al buffer di testo.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Aggiungere un costruttore che imposta il buffer di testo e il provider dell'origine supporto firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono impostati come hardcoded, ma in un'implementazione completa si otterrebbe queste informazioni nella documentazione di linguaggio.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Il metodo helper `CreateSignature()` viene fornito solo a scopo illustrativo.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio sono presenti solo due firme, ognuno dei quali include due parametri. Di conseguenza, questo metodo non è obbligatorio. In un'implementazione più completa, in cui più di un'origine supporto firma è disponibile, questo metodo viene utilizzato per stabilire se l'origine di supporto firma con priorità più alta possibile fornire una firma corrispondente. Se non è possibile, il metodo restituisce null e l'origine successiva priorità più elevata viene chiesto di fornire una corrispondenza.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implementare il `Dispose()` metodo:  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## <a name="implement-the-signature-help-source-provider"></a>Implementare il provider dell'origine supporto firma  
 Il provider di origine supporto firma è responsabile per l'esportazione la parte di componente Managed Extensibility Framework (MEF) e per creare un'istanza di origine supporto firma.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Per implementare il provider di origine supporto firma  
  
1.  Aggiungere una classe denominata `TestSignatureHelpSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di Before = "default".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando il `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## <a name="implement-the-command-handler"></a>Implementare il gestore comando  
 Supporto per la firma viene in genere attivata da una parentesi di apertura carattere "(" carattere e dismissed da parentesi chiuse")". È possibile gestire tali pressioni di tasti eseguendo un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> in modo che attiva una sessione di supporto firma quando viene ricevuta un'apertura carattere di parentesi preceduti da un nome di metodo noto e chiude la sessione quando viene ricevuta una chiusura carattere di parentesi.  
  
#### <a name="to-implement-the-command-handler"></a>Per implementare il gestore del comando  
  
1.  Aggiungere una classe denominata `TestSignatureHelpCommand` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Aggiungere campi privati per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adapter (che consente di aggiungere il gestore comando ai gestori di catena di comando), la visualizzazione di testo, il broker di supporto firma e sessione, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>e la successiva <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Aggiungere un costruttore per inizializzare i campi e per aggiungere il filtro di comando per la catena di filtri di comando.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per attivare la sessione di supporto firma quando il filtro di comando riceve una parentesi di apertura carattere "(" carattere dopo uno dei nomi di metodo noto e per chiudere la sessione quando viene ricevuta una parentesi di chiusura")" mentre la sessione è ancora attiva. In ogni caso, il comando viene inoltrato.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo in modo che venga sempre inoltra il comando.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## <a name="implement-the-signature-help-command-provider"></a>Implementare il provider di comandi supporto firma  
 È possibile fornire il comando Help firma, implementando la <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per creare il gestore comando quando viene creata la visualizzazione di testo.  
  
### <a name="to-implement-the-signature-help-command-provider"></a>Per implementare il provider di comandi supporto firma  
  
1.  Aggiungere una classe denominata `TestSignatureHelpController` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ed esportarlo con la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importa il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (usato per ottenere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto), il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usato per trovare la parola corrente) e il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (per attivare la sessione di supporto firma).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo creando il `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## <a name="build-and-test-the-code"></a>Compilare e testare il codice  
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Per compilare e testare la soluzione SignatureHelpTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include la parola "add" oltre a una parentesi di apertura.  
  
4.  Dopo aver digitato la parentesi di apertura, si dovrebbe essere una descrizione comando che visualizza un elenco di due firme per i `add()` (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)