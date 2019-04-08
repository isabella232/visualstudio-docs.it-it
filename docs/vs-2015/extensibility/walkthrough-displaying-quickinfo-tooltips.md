---
title: 'Procedura dettagliata: Visualizzazione di descrizioni comandi informazioni rapide | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79ce531d36b21ab26cf4c6e6dc76e8c4d98d8763
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968132"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Procedura dettagliata: Visualizzazione delle descrizioni comando di InformazioniBase
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Informazioni rapide è una funzionalità di IntelliSense che consente di visualizzare le firme dei metodi e le descrizioni quando l'utente sposta il puntatore sul nome di un metodo. È possibile implementare funzionalità basata sul linguaggio, ad esempio informazioni rapide che definisce gli identificatori per il quale si desidera fornire descrizioni Informazionibase, e quindi creando una descrizione comando in cui visualizzare il contenuto. È possibile definire QuickInfo nel contesto di un servizio di linguaggio, è possibile definire il tipo di contenuto e l'estensione di nome file e visualizzare le informazioni rapide per solo tale tipo o è possibile visualizzare informazioni rapide per un tipo di contenuto esistente (ad esempio "text"). Questa procedura dettagliata illustra come visualizzare informazioni rapide per il tipo di contenuto "text".  
  
 Nell'esempio di informazioni rapide in questa procedura dettagliata vengono visualizzate le descrizioni comandi quando si sposta il puntatore del mouse su un nome di metodo. Questa progettazione è necessario implementare queste quattro interfacce:  
  
- interfaccia di origine  
  
- interfaccia del provider di origine  
  
- interfaccia del controller  
  
- interfaccia del provider controller  
  
  I provider di origine e il controller vengono parti componente Managed Extensibility Framework (MEF) e sono responsabili per l'esportazione le classi di origine e il controller e l'importazione dei servizi e Broker, ad esempio il <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, che consente di creare il testo della descrizione comando buffer e il <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, che attiva la sessione di informazioni rapide.  
  
  In questo esempio, l'origine di informazioni rapide Usa un elenco hardcoded di nomi di metodi e le descrizioni, ma in implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili per fornire tale contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto C# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual C# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `QuickInfoTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementazione dell'origine di informazioni rapide  
 L'origine di informazioni rapide è responsabile per la raccolta di set di identificatori e le relative descrizioni e aggiungendo il contenuto del buffer di testo della descrizione comando quando viene rilevato uno degli identificatori. In questo esempio, gli identificatori e le relative descrizioni vengono aggiunti solo nel costruttore di origine.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Per implementare l'origine di informazioni rapide  
  
1.  Aggiungere un file di classe e assegnargli il nome `TestQuickInfoSource`.  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Aggiungere le istruzioni import seguenti.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>e denominarla `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  Aggiungere campi per il provider dell'origine Informazionibase, buffer di testo e un set di nomi di metodi e le firme del metodo. In questo esempio, i nomi di metodo e le firme vengono inizializzate le `TestQuickInfoSource` costruttore.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  Aggiungere un costruttore che imposta il provider di origine di informazioni rapide e buffer di testo e quindi popola l'insieme di nomi di metodo e le firme dei metodi e le descrizioni.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. In questo esempio, il metodo trova la parola corrente, o la parola precedente se il cursore si trova alla fine di una riga o un buffer di testo. Se la parola è uno dei nomi di metodo, la descrizione di tale nome viene aggiunto al contenuto QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  È inoltre necessario implementare un metodo Dispose (), poiché <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementazione di un Provider di origine di informazioni rapide  
 Il provider dell'origine QuickInfo serve principalmente per esportare se stessa come parte del componente MEF e creare un'istanza di origine di informazioni rapide. Poiché è una parte del componente MEF, è possibile importare altre parti componente MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Implementare un provider di origine di informazioni rapide  
  
1.  Dichiarare un provider di codice sorgente QuickInfo denominato `TestQuickInfoSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> della descrizione comando informazioni rapide "Source", una <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di Before = "default" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  Due servizi dell'editor, importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, come proprietà di `TestQuickInfoSourceProvider`.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> per restituire un nuovo `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementazione di un Controller di informazioni rapide  
 Controller di Informazionibase determinano quando deve essere visualizzato QuickInfo. In questo esempio, informazioni rapide viene visualizzato quando il puntatore è posizionato sopra di una parola che corrisponde a uno dei nomi di metodo. Il controller QuickInfo implementa un gestore eventi di mouse al passaggio del mouse che attiva una sessione di informazioni rapide.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Per implementare un controller di informazioni rapide  
  
1.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>e denominarla `TestQuickInfoController`.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  Aggiungere campi privati per la visualizzazione di testo, i buffer di testo rappresentati in visualizzazione di testo, la sessione di informazioni rapide e il provider di controller di informazioni rapide.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  Aggiungere un costruttore che imposta i campi e aggiunge il gestore dell'evento del mouse al passaggio del mouse.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  Aggiungere il gestore di eventi di passaggio del mouse del mouse che attiva la sessione di informazioni rapide.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> metodo in modo che rimuove il gestore dell'evento del mouse al passaggio del mouse quando il controller viene scollegato dalla visualizzazione di testo.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> metodo e il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> metodo come metodi vuoti per questo esempio.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementazione del Provider di informazioni rapide Controller  
 Il provider del controller QuickInfo serve principalmente per esportare se stessa come parte del componente MEF e creare un'istanza del controller di informazioni rapide. Poiché è una parte del componente MEF, è possibile importare altre parti componente MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Per implementare il provider di controller di informazioni rapide  
  
1.  Dichiarare una classe denominata `TestQuickInfoControllerProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "Descrizione comando QuickInfo Controller" e un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  Importare <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> come proprietà.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> metodo creando un'istanza del controller di informazioni rapide.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione QuickInfoTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Per compilare e testare la soluzione QuickInfoTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include le parole "Aggiungi" e "sottrarre".  
  
4.  Spostare il puntatore del mouse su una delle occorrenze di "Aggiungi". La firma e la descrizione del `add` metodo deve essere visualizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
