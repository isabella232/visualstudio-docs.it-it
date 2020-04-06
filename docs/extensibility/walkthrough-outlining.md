---
title: 'Procedura dettagliata: Struttura di struttura . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697219"
---
# <a name="walkthrough-outlining"></a>Procedura dettagliata: definizione della struttura
Impostare funzionalità basate sul linguaggio, ad esempio la struttura, definendo i tipi di aree di testo che si desidera espandere o comprimere. È possibile definire aree nel contesto di un servizio di linguaggio oppure definire un'estensione di file e un tipo di contenuto personalizzati e applicare la definizione dell'area solo a tale tipo oppure applicare le definizioni di area a un tipo di contenuto esistente, ad esempio "testo". In questa procedura dettagliata viene illustrato come definire e visualizzare le aree della struttura.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto Managed Extensibility Framework (MEF)

### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto VSIX. Assegnare alla soluzione il nome `OutlineRegionTest`.

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="implement-an-outlining-tagger"></a>Implementare un tagger di strutturaImplement an outlining tagger
 Le aree di struttura sono<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>contrassegnate da un tipo di tag ( ). Questo tag fornisce il comportamento di struttura standard. L'area contornata può essere espansa o compressa. L'area contornata è contrassegnata da un segno più (**+****-**) se è compressa o un segno meno ( ) se è espansa e l'area espansa è delimitata da una linea verticale.

 Nei passaggi seguenti viene illustrato come definire un tagger che crea aree di struttura per tutte le aree delimitate dalle parentesi quadre (**[**,**]**).

### <a name="to-implement-an-outlining-tagger"></a>Per implementare un tagger di strutturaTo implement an outlining tagger

1. Aggiungere un file di classe e assegnargli il nome `OutliningTagger`.

2. Importare gli spazi dei nomi seguenti.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Creare una `OutliningTagger`classe denominata <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>, e fare in modo che implementi :

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Aggiungere alcuni campi per tenere traccia del buffer di testo e dell'istantanea e per accumulare i set di righe che devono essere contrassegnati come aree di struttura. Questo codice include un elenco di Region oggetti (da definire in un secondo momento) che rappresentano le aree di struttura.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Aggiungere un costruttore tagger che inizializza i campi, analizza il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> buffer e aggiunge un gestore eventi all'evento.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> il metodo , che crea un'istanza degli intervalli di tag. In questo esempio si presuppone <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> che gli intervalli nel passato al metodo siano contigui, anche se potrebbe non essere sempre il caso. Questo metodo crea un'istanza di un nuovo intervallo di tag per ognuna delle aree della struttura.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Dichiarare `TagsChanged` un gestore eventi.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Aggiungere `BufferChanged` un gestore eventi <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> che risponde agli eventi analizzando il buffer di testo.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Aggiungere un metodo che analizza il buffer. L'esempio qui fornito è solo a scopo illustrativo. Analizza in modo sincrono il buffer in aree di struttura annidate.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Il metodo helper seguente ottiene un numero intero che rappresenta il livello della struttura, in modo che 1 sia la coppia di parentesi graffe più a sinistra.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Il metodo helper seguente converte un Region (definito più avanti in questo articolo) in un SnapshotSpan.The following helper method translates a Region (defined later in this article) into a SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Il codice seguente è disponibile solo a scopo illustrativo. Definisce una classe PartialRegion che contiene il numero di riga e l'offset dell'inizio di un'area della struttura e un riferimento all'area padre (se presente). Questo codice consente al parser di impostare aree di struttura annidate. Una classe Region derivata contiene un riferimento al numero di riga della fine di un'area della struttura.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementare un provider di taggerImplement a tagger provider
 Esporta un provider di tagger per il tuo tagger. Il provider di `OutliningTagger` tagger crea un per un buffer del `OutliningTagger` tipo di contenuto "testo", altrimenti restituisce un se il buffer ne ha già uno.

### <a name="to-implement-a-tagger-provider"></a>Per implementare un provider di taggerTo implement a tagger provider

1. Creare una `OutliningTaggerProvider` classe <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>denominata che implementa ed esportarla con gli attributi ContentType e TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> il metodo `OutliningTagger` aggiungendo un alle proprietà del buffer.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code
 Per testare questo codice, compilare la soluzione OutlineRegionTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Per compilare e testare la soluzione OutlineRegionTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo. Digitare del testo che includa sia le parentesi quadre di apertura che le parentesi di chiusura.

    ```
    [
       Hello
    ]
    ```

4. Dovrebbe esserci un'area di struttura che includa entrambe le parentesi. Dovrebbe essere possibile fare clic sul segno meno a sinistra della parentesi aperta per comprimere l'area della struttura. Quando l'area è compressa, il simbolo dei puntini di sospensione (*...*) dovrebbe apparire a sinistra dell'area compressa e quando si sposta il puntatore del mouse viene visualizzato un popup contenente il **testo al passaggio** del mouse.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
