---
title: Tempo di esecuzione (Visualizzazione thread) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4131b70a0d76f5245152e397032f55833421c424
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905955"
---
# <a name="execution-time-threads-view"></a>Tempo di esecuzione (visualizzazione Thread)
Questi segmenti nella sequenza temporale della visualizzazione thread rappresentano il tempo di esecuzione, quando il thread è in esecuzione su un core logico nel sistema.  
  
 Le modifiche allo stato del thread vengono rilevate tramite eventi di cambio di contesto del kernel. Event Tracing for Windows (ETW) acquisisce gli stack dei campioni ogni millisecondo. In un segmento verde molto breve è possibile che non venga acquisito alcun campione. Di conseguenza, alcuni segmenti di breve esecuzione possono non visualizzare alcuno stack di chiamate.  
  
 Quando si fa clic su un segmento di esecuzione, il visualizzatore di concorrenza visualizza lo stack di campioni più vicino alla posizione di clic. La posizione dello stack di campioni viene indicata da una freccia di colore nero, o da un accento circonflesso, sopra la sequenza temporale e lo stack di campioni viene visualizzato nella scheda **Corrente**.  
  
 Per visualizzare un profilo di campionamento tradizionale per tutti i segmenti di esecuzione nella visualizzazione corrente, fare clic su **Esecuzione** in Profilo cronologia visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Rapporto profilo di esecuzione](../profiling/execution-profile-report.md)   
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione thread)