---
title: Fasi della pipeline grafica | Microsoft Docs
description: Per risolvere i problemi di rendering, vedere come viene trasformata una chiamata di disegno in ogni fase della pipeline grafica Direct3D.
ms.custom: SEO-VS-2020
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d7a86d93e49f92734bcccd9eefab6ed498734479
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058553"
---
# <a name="graphics-pipeline-stages"></a>Fasi pipeline grafica
La finestra Fasi Pipeline grafica aiuta a comprendere come una singola chiamata di disegno viene trasformata in ogni fase della pipeline grafica Direct3D.

 Questa è la finestra Fasi pipeline:

 ![Un oggetto 3D passa attraverso le fasi della pipeline.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Informazioni sulla finestra Fasi pipeline grafica
 La finestra Fasi pipeline visualizza i risultati di ogni fase della pipeline grafica, separati per ogni chiamata di disegno. In genere i risultati delle fasi nella parte centrale della pipeline sono nascosti e questo rende difficile individuare le cause di un problema di rendering. Visualizzando separatamente ogni fase, la finestra Fasi pipeline consente di individuare facilmente l'origine del problema, ad esempio se una fase di vertex shader ha fatto sì che un oggetto venisse disegnato fuori dallo schermo.

 Dopo avere identificato la fase in cui si verifica il problema, è possibile usare gli altri strumenti di Analizzatore grafica per esaminare il modo in cui i dati sono stati interpretati o trasformati. I problemi di rendering visualizzati nelle fasi della pipeline sono spesso correlati a descrittori di formato vertici non corretti, a programmi shader con bug o a uno stato non configurato correttamente.

### <a name="links-to-related-graphics-objects"></a>Collegamenti a oggetti grafici correlati
 A volte per capire perché una chiamata di disegno interagisce in un determinato modo con la pipeline grafica sono necessarie informazioni di contesto aggiuntive. Per semplificare la ricerca di queste informazioni, la finestra Fasi pipeline grafica contiene collegamenti a uno o più oggetti che forniscono ulteriore contesto correlato a ciò che accade nella pipeline grafica.

- In Direct3D 12 questo oggetto è in genere un elenco di comandi.

- In Direct3D 11 questo oggetto è in genere un contesto dei dispositivi grafici.

  Questi collegamenti fanno parte della firma dell'evento grafico corrente situato nell'angolo superiore sinistro della finestra Fasi pipeline grafica. Seguire i collegamenti per accedere ad altri dettagli sull'oggetto.

### <a name="viewing-and-debugging-shader-code"></a>Visualizzazione e debug del codice dello shader
 Si può visualizzare il codice per Vertex Shader, Hull Shader, Domain Shader, Geometry Shader o Pixel Shader oppure eseguirne il debug, usando i controlli nella parte inferiore della fase corrispondente all'interno della finestra Fasi pipeline.

#### <a name="to-view-a-shaders-source-code"></a>Per visualizzare il codice sorgente di uno shader

- Nella finestra **Fasi pipeline grafica** individuare la fase dello shader che corrisponde allo shader da esaminare. Quindi, sotto l'immagine di anteprima, seguire il collegamento del titolo della fase dello shader. Ad esempio, fare clic sul collegamento **Vertex Shader obj:30** per visualizzare il codice sorgente del vertex shader.

    > [!TIP]
    > Il numero dell'oggetto, **obj:30**, identifica lo shader nell'intera interfaccia di Analizzatore grafica, ad esempio nella tabella oggetti e nella finestra della cronologia pixel.

#### <a name="to-debug-a-shader"></a>Per eseguire il debug di uno shader

- Nella finestra **Fasi pipeline grafica** individuare la fase dello shader che corrisponde allo shader di cui eseguire il debug. Quindi, sotto l'immagine di anteprima, scegliere **Avvia debug**. Questo punto di ingresso nel debugger HLSL corrisponde per impostazione predefinita alla prima chiamata dello shader per la fase corrispondente, ovvero il primo vertice, primitiva o pixel elaborato durante questa chiamata di disegno. È possibile accedere alle altre chiamate dello shader per uno specifico pixel o vertice tramite la **Cronologia pixel grafica**.

### <a name="the-pipeline-stages"></a>Fasi della pipeline
 Nella finestra Fasi pipeline vengono visualizzate solo le fasi della pipeline che erano attive durante la chiamata di disegno. Ogni fase della pipeline grafica trasforma l'input dalla fase precedente e passa il risultato alla fase successiva. La prima fase, ovvero Assemblaggio input, estrae i dati di indici e vertici forniti dall'app e li usa come input. L'ultima fase, ovvero Unione output, combina i pixel di cui è stato eseguito il rendering con il contenuto corrente del buffer frame o della destinazione di rendering per produrre l'immagine finale visualizzata sullo schermo.

> [!NOTE]
> I compute shader non sono supportati nella finestra **Fasi pipeline grafica**.

 **Assembler di input** L'assembler di input legge i dati dell'indice e dei vertici specificati dall'app e lo assembla per l'hardware grafico.

 Nella finestra Fasi pipeline, l'output di Assemblaggio input viene visualizzato come modello wireframe. Per esaminare in dettaglio i risultati, selezionare **Assemblaggio input** nella finestra **Fasi pipeline grafica** per vedere i vertici assemblati in 3D completo usando l'editor modello.

> [!NOTE]
> Se la semantica `POSITION` non è presente nell'output dell'assemblaggio input, nella fase **Assemblaggio input** non verrà visualizzato nulla.

 **Vertex shader** La fase vertex shader elabora i vertici, in genere eseguendo operazioni quali trasformazione, interfaccia e illuminazione. Produce lo stesso numero di vertici che accetta come input.

 Nella finestra Fasi pipeline, l'output di Vertex shader viene visualizzato come immagine raster wireframe. Per esaminare in dettaglio i risultati, selezionare **Vertex shader** nella finestra **Fasi pipeline grafica** per vedere i vertici elaborati nell'editor di immagini.

> [!NOTE]
> Se la semantica `POSITION` o `SV_POSITION` non è presente nell'output di vertex shader, nella fase **Vertex shader** non verrà visualizzato nulla.

 **Hull Shader** (solo Direct3D 11 e Direct3D 12) La fase dello hull shader elabora i punti di controllo che definiscono una superficie di ordine inferiore, ad esempio una linea, un triangolo o un quad. Come output, produce patch geometriche di ordine superiori e costanti patch che vengono passate alla fase del mosaico a funzione fissa.

 La fase Hull shader non viene visualizzata nella finestra Fasi pipeline.

 Fase a **tessellatore** (solo Direct3D 11 e Direct3D 12) La fase a tessellatore è un'unità hardware a funzione fissa (non programmabile) che pre-elabora il dominio rappresentato dall'output dello hull shader. Come output, crea uno schema di campionamento del dominio e un set di primitive più piccole, punti, linee e triangoli, che connettono in questi campioni.

 La fase del mosaico non viene visualizzata nella finestra Fasi pipeline.

 **Domain Shader** (solo Direct3D 11 e Direct3D 12) La fase domain shader elabora le patch di geometria di ordine superiore dello shader Hull, insieme ai fattori a schema a fasi della fase a tessellazione. I fattori a mosaico possono essere includere fattori di input della fase di mosaico così come fattori di output. Come output, calcola la posizione del vertice di un punto sulla patch di output in base ai fattori a mosaico.

 La fase Domain shader non viene visualizzata nella finestra Fasi pipeline.

 **Shader geometrico** La fase geometry shader elabora intere primitive, ovvero punti, linee o triangoli, insieme ai dati dei vertici facoltativi per le primitive adiacenti al bordo. A differenza dei vertex shader, i geometry shader possono produrre più o meno primitive che accettano come input.

 Nella finestra Fasi pipeline, l'output di Geometry Shader viene visualizzato come immagine raster wireframe. Per esaminare in dettaglio i risultati, selezionare **Geometry shader** nella finestra **Fasi pipeline grafica** per vedere le primitive elaborate nell'editor di immagini.

 **Fase di output del flusso** La fase di output del flusso può intercettare le primitive trasformate prima della rasterizzazione e scriverle in memoria. da qui i dati possono essere ricircolati come input nelle fasi precedenti della pipeline grafica o essere letti dalla CPU.

 La fase Output flusso non viene visualizzata nella finestra Fasi pipeline.

 **Fase di rasterizzazione** La fase di rasterizzazione è un'unità hardware a funzione fissa (non programmabile) che converte primitive vettoriali( punti, linee, triangoli) in un'immagine raster eseguendo la conversione della linea di analisi. Durante la rasterizzazione i vertici vengono trasformati nello spazio del ritaglio omogeneo e tagliati. Come output, viene eseguito il mapping dei pixel shader e gli attributi dei vertici della primitiva vengono interpolati e preparati per il pixel shader.

 La fase di rasterizzazione non viene visualizzata nella finestra Fasi pipeline.

 **Pixel shader** La pixel shader elabora primitive rasterizzate insieme ai dati dei vertici interpolati per generare valori per pixel, ad esempio colore e profondità.

 Nella finestra Fasi pipeline, l'output di Pixel shader viene visualizzato come un'immagine raster a colori. Per esaminare in dettaglio i risultati, selezionare **Pixel shader** nella finestra **Fasi pipeline grafica** per vedere le primitive elaborate nell'editor di immagini.

 **Unione dell'output** La fase di unione dell'output combina l'effetto dei pixel di cui è stato appena eseguito il rendering con il contenuto esistente dei buffer corrispondenti( colore, profondità e stencil) per produrre nuovi valori in questi buffer.

 Nella finestra Fasi pipeline, l'output di Unione output viene visualizzato come un'immagine raster a colori. Per esaminare in dettaglio i risultati, selezionare **Unione output** nella finestra **Fasi pipeline grafica** per vedere il buffer frame unito.

### <a name="vertex-and-geometry-shader-preview"></a>Anteprima vertex e geometry shader
 Quando si seleziona la fase vertex shader o geometry shader nella finestra **Fasi** pipeline, è possibile visualizzare gli input e gli output dello shader nel pannello seguente.  Qui sono disponibili informazioni dettagliate sull'elenco dei vertici forniti agli shader dopo che sono stati assemblati dalla fase dell'assembler di input.

 ![Visualizzatore del buffer di input delle fasi del vertex shader](media/gfx_diag_vertex_shader_inbuffers.png)

 Per visualizzare i risultati della fase Vertex shader, scegliere l'anteprima corrispondente per visualizzare un wireframe rasterizzato a dimensioni intere della mesh dopo la trasformazione.

 ![Anteprima dei risultati delle fasi del vertex shader](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Oggetti mancanti a causa dello sfondo Vertex](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Procedura dettagliata: Debug degli errori di rendering dovuti allo sfondo](walkthrough-debugging-rendering-errors-due-to-shading.md)