---
title: Segmento della cronologia vuoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac39a776cb7e6c2c9cbce648c0b3ca3ebc86783
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54770745"
---
# <a name="empty-timeline-segment"></a>Segmento della cronologia vuoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nel visualizzatore di concorrenza, il motivo per cui una sezione della sequenza temporale è vuota (presenta uno sfondo bianco) dipende dal tipo di canale.  
  
-   Per un canale di thread di CPU, significa che il thread non esisteva in quella parte della sequenza temporale. Se si è interessati al thread, è possibile trovare la relativa sezione in esecuzione usando il controllo zoom o lo scorrimento orizzontale.  
  
-   Per un canale I/O, significa che non si è verificato alcun accesso al disco per conto del processo di destinazione in quel momento.  
  
-   Per un canale di DirectX, significa che non è stata eseguita alcuna operazione GPU per conto del processo di destinazione in quella parte della sequenza temporale.  
  
-   Per un canale di marcatore, significa che non sono stati generati marcatori.  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md)  (Visualizzazione thread)  
 [Zoom Control (Threads View)](../profiling/zoom-control-threads-view.md) (Controllo zoom (visualizzazione Thread))
