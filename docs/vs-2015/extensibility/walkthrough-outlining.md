---
title: 'Procedura dettagliata: Struttura | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6737d9fffa1f0f38fab57edd4031647d0cc1510e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529469"
---
# <a name="walkthrough-outlining"></a>Procedura dettagliata: definizione della struttura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: struttura](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-outlining).  
  
È possibile implementare funzionalità basate sul linguaggio, ad esempio definendo i tipi di aree di testo che si desidera espandere o comprimere la struttura. È possibile definire le aree nel contesto di un servizio di linguaggio, è possibile definire il tipo di contenuto e l'estensione di nome file e applicare la definizione dell'area da solo a quel tipo o è possibile applicare le definizioni di area a un tipo di contenuto esistente (ad esempio "text"). Questa procedura dettagliata illustra come definire e visualizzare le aree della struttura.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto VSIX. Denominare la soluzione `OutlineRegionTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementare un Tagger della struttura  
 Aree della struttura sono contrassegnate da un tipo di tag (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Questo tag fornisce lo standard della struttura di comportamento. L'area può essere espansi o compressi. L'area viene contrassegnato da un segno più, se è compresso o un segno meno se viene espanso e l'area espansa è delimitata da una linea verticale.  
  
 La procedura seguente illustra come definire un tagger che crea aree della struttura per tutte le aree che sono delimitate da "[" e "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Per implementare un tagger della struttura  
  
1.  Aggiungere un file di classe e denominarla `OutliningTagger`.  
  
2.  Importare gli spazi dei nomi seguenti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3.  Creare una classe denominata `OutliningTagger`, e che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4.  Aggiungere alcuni campi per tenere traccia il buffer di testo e lo snapshot e per accumulare i set di righe che devono essere contrassegnate come aree della struttura. Questo codice include un elenco di oggetti area (devono essere definite in un secondo momento) che rappresentano le aree della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5.  Aggiungere un costruttore tagger che inizializza i campi, analizza il buffer e aggiunge un gestore eventi per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> si estende su metodo, che crea un'istanza del tag. Questo esempio si presuppone che gli intervalli nel <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passato al metodo sono contigui, anche se potrebbe non essere sempre la scelta. Questo metodo crea un'istanza di un nuovo intervallo di tag per ognuna delle aree della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7.  Dichiarare un `TagsChanged` gestore dell'evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8.  Aggiungere un `BufferChanged` gestore dell'evento che risponde a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventi analizzando il buffer di testo.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Aggiungere un metodo che analizza il buffer. L'esempio riportato di seguito è solo a scopo illustrativo. Analizza in modo sincrono il buffer in aree della struttura annidate.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Il metodo helper seguente ottiene un intero che rappresenta il livello di struttura, in modo che la coppia di parentesi più a sinistra è 1.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Il metodo helper seguente converte un'area (definita più avanti in questo argomento) in un elemento SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Il codice seguente è solo a scopo illustrativo. Definisce una classe PartialRegion che contiene il numero di riga e l'offset dell'inizio di un'area della struttura, nonché un riferimento all'area del padre (se presente). In questo modo il parser configurare annidati aree della struttura. Una classe derivata di area contiene un riferimento al numero di riga di fine di un'area della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementazione di un Provider di Tagger  
 È necessario esportare un provider di tagger per il tagger. Il provider di tagger crea un' `OutliningTagger` per un buffer del tipo di contenuto "text", o restituisce altro un `OutliningTagger` se il buffer contiene già uno.  
  
#### <a name="to-implement-a-tagger-provider"></a>Implementare un provider di tagger  
  
1.  Creare una classe denominata `OutliningTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ed esportarlo con gli attributi ContentType e TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo aggiungendo un `OutliningTagger` alle proprietà del buffer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione OutlineRegionTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Per compilare e testare la soluzione OutlineRegionTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo. Digitare un testo che include parentesi graffa di apertura e la parentesi graffa di chiusura.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Deve essere presente un'area della struttura che include entrambe le parentesi graffe. È necessario essere in grado di fare clic sul segno meno a sinistra della parentesi graffa aperta per comprimere l'area della struttura. Quando l'area viene compressa, il simbolo di puntini di sospensione (...) deve apparire a sinistra dell'area compressa e una finestra popup contenente il testo **passare il puntatore di testo** deve essere visualizzato quando si sposta il puntatore sui puntini di sospensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

