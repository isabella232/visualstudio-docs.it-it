---
title: 'Procedura dettagliata: struttura | Microsoft Docs'
description: Informazioni su come definire e visualizzare le aree della struttura nel contesto di un servizio di linguaggio o per l'estensione del nome file e il tipo di contenuto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: aa66d3b32f6992cb3a5db13bc2b7ee4d5cd9294c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951186"
---
# <a name="walkthrough-outlining"></a>Procedura dettagliata: definizione della struttura
Configurare le funzionalità basate sul linguaggio, ad esempio la struttura, definendo i tipi di aree di testo che si desidera espandere o comprimere. È possibile definire le aree nel contesto di un servizio di linguaggio oppure definire l'estensione del nome di file e il tipo di contenuto e applicare la definizione di area solo a tale tipo oppure applicare le definizioni delle aree a un tipo di contenuto esistente, ad esempio "testo". Questa procedura dettagliata illustra come definire e visualizzare le aree della struttura.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto di Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX. Assegnare alla soluzione il nome `OutlineRegionTest`.

2. Aggiungere un modello di elemento classificatore editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="implement-an-outlining-tagger"></a>Implementare un codificatore della struttura
 Le aree della struttura sono contrassegnate da un tipo di tag ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Questo tag fornisce il comportamento della struttura standard. È possibile espandere o comprimere l'area delineata. L'area delineata è contrassegnata da un segno di addizione ( **+** ) se è compresso o un segno meno ( **-** ) se è espanso e l'area espansa è delimitata da una linea verticale.

 Nei passaggi seguenti viene illustrato come definire un tag che crea aree della struttura per tutte le aree delimitate dalle parentesi quadre (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Per implementare un codificatore della struttura

1. Aggiungere un file di classe e assegnargli il nome `OutliningTagger`.

2. Importare gli spazi dei nomi seguenti.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Creare una classe denominata `OutliningTagger` e implementarla <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Aggiungere alcuni campi per tenere traccia del buffer di testo e dello snapshot e per accumulare i set di righe che devono essere contrassegnati come aree della struttura. Questo codice include un elenco di oggetti Region (da definire in seguito) che rappresentano le aree della struttura.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Aggiungere un costruttore di tag che Inizializza i campi, analizza il buffer e aggiunge un gestore eventi all' <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo, che crea un'istanza degli intervalli di tag. In questo esempio si presuppone che gli intervalli nell'oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passato al metodo siano contigui, sebbene non sia sempre il caso. Questo metodo crea un'istanza di un nuovo intervallo di tag per ognuna delle aree della struttura.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Dichiarare un `TagsChanged` gestore eventi.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Aggiungere un `BufferChanged` gestore eventi che risponde agli eventi analizzando <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> il buffer di testo.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Aggiungere un metodo che analizza il buffer. L'esempio riportato di seguito è a solo illustrazione. Il buffer viene analizzato in modo sincrono nelle aree della struttura nidificata.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Il metodo helper seguente ottiene un valore integer che rappresenta il livello della struttura, in modo che 1 sia la coppia di parentesi graffa più a sinistra.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Il metodo helper seguente converte un'area (definita più avanti in questo articolo) in un elemento SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Il codice seguente è a solo illustrazione. Definisce una classe PartialRegion che contiene il numero di riga e l'offset dell'inizio di un'area della struttura e un riferimento all'area padre (se presente). Questo codice consente al parser di configurare aree della struttura nidificata. Una classe Region derivata contiene un riferimento al numero di riga alla fine di un'area della struttura.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementare un provider di tag
 Esporta un provider di tag per il tag. Il provider del tag crea un oggetto `OutliningTagger` per un buffer del tipo di contenuto "Text"; in caso contrario, restituisce `OutliningTagger` se il buffer ne contiene già uno.

### <a name="to-implement-a-tagger-provider"></a>Per implementare un provider di tag

1. Creare una classe denominata `OutliningTaggerProvider` che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ed esporti gli attributi ContentType e TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo aggiungendo un oggetto `OutliningTagger` alle proprietà del buffer.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione OutlineRegionTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Per compilare e testare la soluzione OutlineRegionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo. Digitare il testo che include le parentesi quadre di apertura e di chiusura.

    ```
    [
       Hello
    ]
    ```

4. Deve essere presente un'area della struttura che include entrambe le parentesi quadre. Si dovrebbe essere in grado di fare clic sul segno meno a sinistra della parentesi aperta per comprimere l'area della struttura. Quando l'area è compressa, il simbolo dei puntini di sospensione (*...*) viene visualizzato a sinistra dell'area compressa e viene visualizzato un popup contenente il **testo al passaggio del mouse** quando si sposta il puntatore sui puntini di sospensione.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
