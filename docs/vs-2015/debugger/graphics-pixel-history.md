---
title: Cronologia Pixel grafica | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b37dab129c5eb19825746177cb30a5e20493399
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527884"
---
# <a name="graphics-pixel-history"></a>Cronologia pixel grafica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [cronologia Pixel grafica](https://docs.microsoft.com/visualstudio/debugger/graphics/graphics-pixel-history).  
  
La finestra Cronologia pixel grafica disponibile in Analizzatore grafica di Visual Studio consente di comprendere in che modo uno specifico pixel viene interessato dagli eventi Direct3D che si verificano durante un frame del gioco o dell'app.  
  
 Questa è la finestra Cronologia pixel:  
  
 ![Un pixel con tre eventi Direct3D nella cronologia. ](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Informazioni sulla finestra Cronologia pixel  
 Con la Cronologia pixel è possibile analizzare come un pixel specifico della destinazione di rendering sia interessato dagli eventi Direct3D durante un frame. È possibile associare con precisione un problema di rendering a un evento specifico di Direct3D, anche quando gli eventi successivi, o le primitive successive nello stesso evento, continuano a modificare il valore del colore finale del pixel. Ad esempio, è possibile eseguire il rendering errato di un pixel che viene quindi nascosto da un altro pixel semitrasparente in modo che i loro colori vengano fusi insieme nel framebuffer. Questo tipo di problema sarebbe difficile da diagnosticare se si disponesse solo del contenuto finale della destinazione di rendering come indicazione.  
  
 Nella finestra Cronologia pixel viene visualizzata la cronologia completa di un pixel nel corso del frame selezionato. Il **Buffer Frame finale** nella parte superiore della finestra viene visualizzato il colore che viene scritto nel framebuffer alla fine del frame, insieme a informazioni aggiuntive sul pixel quali il frame che proviene da una e la schermata coordinate. Quest'area contiene anche il **rendering alfa** casella di controllo. Quando questa casella di controllo è selezionata, il **Buffer Frame finale** valori colore intermedio e colore vengono visualizzati con trasparenza su un modello a scacchiera. Se la casella di controllo è deselezionata, il canale alfa dei valori di colore viene ignorato.  
  
 La parte inferiore della finestra Visualizza gli eventi che avevano possibilità di modificare il colore del pixel, insieme con il **iniziale** e **finale** pseudo-eventi che rappresentano i valori di colore iniziale e finale di il pixel nel framebuffer. Il valore del colore iniziale è determinato dal primo evento che ha modificato il colore del pixel (in genere un evento `Clear`). Un pixel ha sempre questi due pseudo-eventi nella cronologia, anche quando non è stato interessato da altri eventi. Quando altri eventi possono influire sul pixel, vengono visualizzati tra il **iniziale** e **finale** gli eventi. È possibile espandere gli eventi per visualizzarne i dettagli. Per gli eventi semplici come quelli che eliminano una destinazione di rendering, l'effetto dell'evento è semplicemente un valore di colore. Gli eventi più complessi come le chiamate di disegno generano una o più primitive che possono contribuire al colore del pixel.  
  
 Le primitive che sono state create dall'evento vengono identificate dal tipo primitivo e dall'indice, con il numero totale di primitive per l'oggetto. Ad esempio, un identificatore, ad esempio **triangolo (1456) di (6214)** significa che la primitiva corrisponde al 1456 ° triangolo in un oggetto che è costituito da 6214 triangoli. A sinistra di ciascun identificatore di primitiva è presente un'icona che riepiloga l'effetto della primitiva sul pixel. Le primitive che influiscono sul colore del pixel vengono rappresentate da un rettangolo arrotondato che viene riempito con il colore risultante. Le primitive escluse dall'influenzare il colore del pixel vengono rappresentate da icone che indicano il motivo per cui il pixel è stato escluso. Queste icone vengono descritte nella sezione [esclusione primitiva](../debugger/graphics-pixel-history.md#exclusion) più avanti in questo articolo.  
  
 È possibile espandere ogni primitiva per esaminare in che modo l'output del pixel shader è stato unito al colore del pixel esistente per produrre il colore risultante. A questo punto è possibile esaminare o eseguire il debug del codice del pixel shader associato alla primitiva ed è inoltre possibile espandere il nodo di vertex shader per esaminare l'input del vertex shader.  
  
###  <a name="exclusion"></a> Esclusione di primitive  
 Se una primitiva viene esclusa dall'influenzare il colore del pixel, l'esclusione può verificarsi per diversi motivi. Ogni motivo è rappresentato da un'icona descritta nella tabella seguente:  
  
|Icona|Motivo dell'esclusione|  
|----------|--------------------------|  
|![Icona di errore test di profondità. ](../debugger/media/vsg-hist-icon-failed-depth.png "vsg_hist_icon_failed_depth")|Pixel escluso poiché non ha superato il test di profondità.|  
|![Icona di errore test di ritaglio. ](../debugger/media/vsg-hist-icon-failed-scissor.png "vsg_hist_icon_failed_scissor")|Pixel escluso poiché non ha superato il test di ritaglio.|  
|![Icona di errore test di stencil. ](../debugger/media/vsg-hist-icon-failed-stencil.png "vsg_hist_icon_failed_stencil")|Pixel escluso poiché non ha superato il test di stencil.|  
  
### <a name="draw-call-exclusion"></a>Esclusione di chiamata di disegno  
 Se tutte le primitive di una chiamata di disegno vengono escluse dall'influenzare la destinazione di rendering in quanto non superano un test, la chiamata di disegno non può essere espansa e accanto a tale chiamata viene visualizzata un'icona che corrisponde al motivo dell'esclusione. I motivi dell'esclusione della chiamata di disegno assomigliano a quelli dell'esclusione delle primitive e le relative icone sono simili.  
  
### <a name="viewing-and-debugging-shader-code"></a>Visualizzazione e debug del codice dello shader  
 È possibile visualizzare il codice per vertex shader, hull shader, domain shader, geometry shader o pixel shader oppure eseguirne il debug usando i comandi sotto la primitiva associata allo shader.  
  
##### <a name="to-view-a-shaders-source-code"></a>Per visualizzare il codice sorgente di uno shader  
  
1.  Nel **cronologia Pixel grafica** finestra, individuare la chiamata di disegno che corrisponde allo shader si desidera esaminare ed espanderla.  
  
2.  Sotto la chiamata di disegno appena espansa selezionare una primitiva che mostra il problema a cui si è interessati ed espanderla.  
  
3.  Sotto la primitiva si è interessati, seguire il collegamento del titolo dello shader, ad esempio, fare clic sul collegamento **Vertex Shader obj:30** per visualizzare il codice sorgente del vertex shader.  
  
    > [!TIP]
    >  Il numero dell'oggetto, **obj:30**, identifica lo shader nell'intera interfaccia di Analizzatore grafica, ad esempio la finestra fasi oggetto tabelle e pipeline.  
  
##### <a name="to-debug-a-shader"></a>Per eseguire il debug di uno shader  
  
1.  Nel **cronologia Pixel grafica** finestra, individuare la chiamata di disegno che corrisponde allo shader si desidera esaminare ed espanderla.  
  
2.  Quindi, sotto la chiamata di disegno appena espansa selezionare una primitiva che mostra il problema a cui si è interessati ed espanderla.  
  
3.  Sotto la primitiva si è interessati, scegliere **Avvia debug**. Questo punto di ingresso nel debugger HLSL corrisponde per impostazione predefinita alla prima chiamata dello shader per la primitiva corrispondente, ovvero il primo pixel o vertice elaborato dallo shader. Esiste un solo pixel associato alla primitiva, ma esistono più chiamate del vertex shader per linee e triangoli.  
  
     Per eseguire il debug la chiamata del vertex shader per un vertice specifico, espandere il titolo vertexshader e individuare il vertice a cui si è interessati, quindi scegliere **Avvia debug** accanto a esso.  
  
### <a name="links-to-graphics-objects"></a>Collegamenti a oggetti grafici  
 Per comprendere gli eventi grafici nella cronologia del pixel, potrebbero essere necessarie informazioni sullo stato del dispositivo al momento dell'evento o sugli oggetti Direct3D a cui fa riferimento l'evento. Per ogni evento nella cronologia del pixel, la **cronologia Pixel grafica** vengono forniti i collegamenti per il dispositivo attualmente dello stato e agli oggetti correlati.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Oggetti mancanti a causa dello stato del dispositivo](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [Procedure dettagliate: debug degli errori di rendering dovuti allo sfondo](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



