---
title: 'Procedura dettagliata: struttura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201962"
---
# <a name="walkthrough-outlining"></a>Procedura dettagliata: definizione della struttura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile implementare funzionalità basate su linguaggio, ad esempio la struttura, definendo i tipi di aree di testo che si desidera espandere o comprimere. È possibile definire le aree nel contesto di un servizio di linguaggio oppure è possibile definire l'estensione del nome di file e il tipo di contenuto e applicare la definizione di area solo a tale tipo oppure applicare le definizioni delle aree a un tipo di contenuto esistente, ad esempio "testo". Questa procedura dettagliata illustra come definire e visualizzare le aree della struttura.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1. Creare un progetto VSIX. Assegnare alla soluzione il nome `OutlineRegionTest`.  
  
2. Aggiungere un modello di elemento classificatore editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementazione di un tag di struttura  
 Le aree della struttura sono contrassegnate da un tipo di tag ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Questo tag fornisce il comportamento della struttura standard. È possibile espandere o comprimere l'area delineata. L'area delineata è contrassegnata da un segno di addizione se è compresso o un segno meno se è espanso e l'area espansa è delimitata da una linea verticale.  
  
 Nei passaggi seguenti viene illustrato come definire un tag che crea aree della struttura per tutte le aree delimitate da "[" e "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Per implementare un codificatore della struttura  
  
1. Aggiungere un file di classe e assegnargli il nome `OutliningTagger`.  
  
2. Importare gli spazi dei nomi seguenti.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Creare una classe denominata `OutliningTagger` e implementarla <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Aggiungere alcuni campi per tenere traccia del buffer di testo e dello snapshot e per accumulare i set di righe che devono essere contrassegnati come aree della struttura. Questo codice include un elenco di oggetti Region (da definire in seguito) che rappresentano le aree della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Aggiungere un costruttore di tag che Inizializza i campi, analizza il buffer e aggiunge un gestore eventi all' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo, che crea un'istanza degli intervalli di tag. In questo esempio si presuppone che gli intervalli nell'oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passato al metodo siano contigui, anche se ciò potrebbe non essere sempre il caso. Questo metodo crea un'istanza di un nuovo intervallo di tag per ognuna delle aree della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Dichiarare un `TagsChanged` gestore eventi.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Aggiungere un `BufferChanged` gestore eventi che risponde agli eventi analizzando <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> il buffer di testo.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Aggiungere un metodo che analizza il buffer. L'esempio riportato di seguito è a solo illustrazione. Il buffer viene analizzato in modo sincrono nelle aree della struttura nidificata.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. Il metodo helper seguente ottiene un valore integer che rappresenta il livello della struttura, in modo che 1 sia la coppia di parentesi graffa più a sinistra.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. Il metodo helper seguente converte un'area (definita più avanti in questo argomento) in un elemento SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. Il codice seguente è a solo illustrazione. Definisce una classe PartialRegion che contiene il numero di riga e l'offset dell'inizio di un'area della struttura e anche un riferimento all'area padre (se presente). In questo modo il parser è in grado di configurare aree della struttura nidificata. Una classe Region derivata contiene un riferimento al numero di riga alla fine di un'area della struttura.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementazione di un provider di tag  
 È necessario esportare un provider di tag per il tag. Il provider del tag crea un oggetto `OutliningTagger` per un buffer del tipo di contenuto "Text"; in caso contrario, restituisce `OutliningTagger` se il buffer ne contiene già uno.  
  
#### <a name="to-implement-a-tagger-provider"></a>Per implementare un provider di tag  
  
1. Creare una classe denominata `OutliningTaggerProvider` che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ed esporti gli attributi ContentType e TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo aggiungendo un oggetto `OutliningTagger` alle proprietà del buffer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione OutlineRegionTest ed eseguirla nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Per compilare e testare la soluzione OutlineRegionTest  
  
1. Compilare la soluzione.  
  
2. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3. Creare un file di testo. Digitare il testo che include sia la parentesi graffa di apertura che la parentesi graffa di chiusura.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Deve essere presente un'area della struttura che include entrambe le parentesi graffe. Si dovrebbe essere in grado di fare clic sul segno meno a sinistra della parentesi graffa aperta per comprimere l'area della struttura. Quando l'area è compressa, il simbolo dei puntini di sospensione (...) viene visualizzato a sinistra dell'area compressa e viene visualizzato un popup contenente il **testo al passaggio del mouse** quando si sposta il puntatore sui puntini di sospensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
