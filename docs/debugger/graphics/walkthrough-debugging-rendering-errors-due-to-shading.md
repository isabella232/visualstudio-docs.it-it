---
title: "Procedura dettagliata: Debug degli errori di rendering dovuti all'ombreggiatura | Microsoft Docs"
description: Seguire un'indagine che trova un bug dello shader. Mostra l'uso di Visual Studio Diagnostica della grafica, inclusa la cronologia dei pixel della grafica e il debugger HLSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9b8e62cbf7d1dfb931c96a280c7b9bfcc1f73468f4944c438db6ff3e7d2546f9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362606"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Procedura dettagliata: Debug degli errori di rendering dovuti allo sfondo
Questa procedura dettagliata illustra come usare Diagnostica della grafica per analizzare un oggetto colorato in modo non corretto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a causa di un bug dello shader.

 Questa procedura dettagliata illustra come:

- Esaminare il documento del log di grafica per identificare i pixel che presentano il problema.

- Usare la finestra **Cronologia pixel grafica** per esaminare in dettaglio lo stato dei pixel.

- Usare il **debugger HLSL** per esaminare pixel shader e vertex shader.

## <a name="scenario"></a>Scenario
 Una colorazione non corretta per gli oggetti si verifica in genere quando un vertex shader passa informazioni errate o incomplete a un pixel shader.

 In questo scenario è stato aggiunto di recente un oggetto all'app. Sono stati aggiunti anche un nuovo vertice e pixel shader per trasformare l'oggetto e assegnargli un aspetto univoco. Quando si esegue l'app durante un test, l'oggetto viene visualizzato in nero a tinta unita. Usando gli strumenti di Diagnostica della grafica, è possibile acquisire il problema in un log di grafica in modo da poter eseguire il debug dell'app. Il problema è simile a questa immagine nell'app:

 ![Rendering dell'oggetto con colori non corretti.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Analisi
 Utilizzando gli strumenti di diagnostica della grafica, è possibile caricare il documento del log di grafica per controllare i frame acquisiti durante il test.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Per esaminare un frame in un log di grafica

1. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricare un log di grafica con un frame che mostra il modello mancante. Viene visualizzata una nuova finestra del documento del log grafico in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Nella parte superiore di questa finestra è presente l'output della destinazione di rendering del frame selezionato. Nella parte inferiore è presente **Elenco frame**, che visualizza ogni frame acquisito come immagine di anteprima.

2. In **Elenco frame** selezionare una cornice in cui l'oggetto non abbia l'aspetto corretto. La destinazione di rendering viene aggiornata per riflettere la selezione del frame. In questo scenario, la finestra del documento del log di grafica è simile a questa immagine:

    ![Documento del log di grafica in Visual Studio.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Dopo aver selezionato un frame che dimostra il problema, è possibile usare la finestra **Cronologia pixel grafica** per diagnosticarlo. La finestra **Cronologia pixel grafica** mostra le primitive che potrebbero aver avuto un effetto su un pixel specifico, i relativi shader e gli effetti corrispondenti sulla destinazione di rendering, in ordine cronologico.

#### <a name="to-examine-a-pixel"></a>Per esaminare un pixel

1. Aprire la finestra **Cronologia pixel grafica** . Scegliere **Cronologia pixel** sulla barra degli strumenti **Diagnostica grafica**.

2. Selezionare un pixel da esaminare. Nella finestra del documento del log di grafica selezionare uno dei pixel nell'oggetto non colorato correttamente:

    ![La selezione di un pixel comporta la visualizzazione di informazioni sulla relativa cronologia.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    La finestra **Cronologia pixel grafica** viene aggiornata in base al pixel selezionato. In questo scenario la finestra **Cronologia pixel grafica** ha questo aspetto:

    ![La cronologia pixel mostra un evento DrawIndexed.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Si noti che il risultato del pixel shader è completamente nero opaco (0, 0, 0, 1)  e che Output **Merger** ha combinato questo pixel shader con il colore Precedente del pixel in modo che anche **Result** sia completamente opaco.

   Dopo aver esaminato un pixel colorato in modo errato e aver appurato che il colore dell'output del pixel shader non è quello previsto, è possibile usare il debugger HLSL per esaminare il pixel shader e scoprire cosa è successo al colore dell'oggetto. È possibile usare il debugger HLSL per esaminare lo stato delle variabili HLSL durante l'esecuzione, eseguire il codice HLSL un'istruzione alla volta e impostare i punti di interruzione per facilitare la diagnosi del problema.

#### <a name="to-examine-the-pixel-shader"></a>Per esaminare il pixel shader

1. Avviare il debug del pixel shader. Nella finestra **Cronologia pixel grafica** , nella primitiva dell'oggetto, accanto a **Pixel shader** scegliere il pulsante **Avvia debug** .

2. In questo scenario, poiché il pixel shader passa semplicemente il colore dal vertex shader, è facile concludere che il pixel shader non è l'origine del problema.

3. Posizionare il puntatore su `input.color`. Si noti che il relativo valore è nero completamente opaco (0, 0, 0, 1).

    ![Il membro "color" di "input" non è nero.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    In questo scenario un'analisi rivela che il colore non corretto è probabilmente il risultato di un vertex shader che non fornisce informazioni corrette sul colore perché possano essere utilizzate dal pixel shader.

   Una volta determinato che il vertex shader non fornisce probabilmente le informazioni corrette al pixel shader, il passaggio successivo consiste nell'esaminare il vertex shader.

#### <a name="to-examine-the-vertex-shader"></a>Per esaminare il vertex shader

1. Avviare il debug del vertex shader. Nella finestra **Cronologia pixel grafica** , nella primitiva dell'oggetto, accanto a **Vertex shader** scegliere il pulsante **Avvia debug** .

2. Individuare la struttura di output del vertex shader, ovvero l'input per il pixel shader. In questo scenario, il nome di questa struttura è `output`. Esaminare il codice di vertex shader e notare che il membro `color` della struttura `output` è stato impostato in modo esplicito su nero completamente opaco, probabilmente a causa delle attività di debug di un utente.

3. Verificare che il membro del colore non venga mai copiato dalla struttura di input. Poiché il valore di `output.color` viene impostato su nero completamente opaco immediatamente prima che venga restituita la struttura `output`, è consigliabile verificare se il valore di `output` non sia stato correttamente inizializzato in una riga precedente. Eseguire il codice di vertex shader un'istruzione alla volta fino al raggiungimento della riga tramite cui si imposta `output.color` su nero durante l'analisi del valore di `output.color`. Si noti che il valore di `output.color` non viene inizializzato fino a quando non viene impostato su nero. In questo modo viene confermato che la riga di codice tramite cui si imposta `output.color` su nero deve essere modificata, anziché eliminata.

    ![Il valore di "output.color" è nero.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   Una volta determinato che la causa del problema di rendering è che il vertex shader non fornisce un valore di colore corretto al pixel shader, è possibile utilizzare queste informazioni per correggere il problema. In questo scenario è possibile correggere l'errore modificando il codice seguente nel vertex shader

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 in

```hlsl
output.color = input.color;
```

 Questo codice passa semplicemente il colore del vertice dai vertici dell'oggetto senza modifiche. Vertex shader più complessi potrebbero modificare il colore prima di passarlo. Il codice corretto del vertex shader dovrebbe essere simile al seguente:

 ![Codice del Vertex shader corretto.](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Dopo aver corretto il codice, ricompilare ed eseguire l'app per verificare che il problema di rendering sia stato risolto:

 ![Rendering dell'oggetto con colori corretti.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
