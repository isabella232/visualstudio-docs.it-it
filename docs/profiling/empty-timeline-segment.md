---
title: Segmento della cronologia vuoto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad8d87c0574ac2c7671012fff6a81a568d6bff5f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764530"
---
# <a name="empty-timeline-segment"></a>Segmento della sequenza temporale vuoto
Nel visualizzatore di concorrenza, il motivo per cui una sezione della sequenza temporale è vuota (presenta uno sfondo bianco) dipende dal tipo di canale.  
  
-   Per un canale di thread di CPU, significa che il thread non esisteva in quella parte della sequenza temporale. Se si è interessati al thread, è possibile trovare la relativa sezione in esecuzione usando il controllo zoom o lo scorrimento orizzontale.  
  
-   Per un canale I/O, significa che non si è verificato alcun accesso al disco per conto del processo di destinazione in quel momento.  
  
-   Per un canale di DirectX, significa che non è stata eseguita alcuna operazione GPU per conto del processo di destinazione in quella parte della sequenza temporale.  
  
-   Per un canale di marcatore, significa che non sono stati generati marcatori.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)   
 [Controllo Zoom (visualizzazione Thread)](../profiling/zoom-control-threads-view.md)