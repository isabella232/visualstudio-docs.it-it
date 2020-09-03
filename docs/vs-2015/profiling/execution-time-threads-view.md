---
title: Tempo di esecuzione (Visualizzazione thread) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4306e030c2f48d87b12ba6338a847dc9e9aa892
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179036"
---
# <a name="execution-time-threads-view"></a>Tempo di esecuzione (visualizzazione Thread)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale della visualizzazione thread rappresentano il tempo di esecuzione, quando il thread è in esecuzione su un core logico nel sistema.  
  
 Le modifiche allo stato del thread vengono rilevate tramite eventi di cambio di contesto del kernel. Event Tracing for Windows (ETW) acquisisce gli stack dei campioni ogni millisecondo. In un segmento verde molto breve è possibile che non venga acquisito alcun campione. Di conseguenza, alcuni segmenti di breve esecuzione possono non visualizzare alcuno stack di chiamate.  
  
 Quando si fa clic su un segmento di esecuzione, il visualizzatore di concorrenza visualizza lo stack di campioni più vicino alla posizione di clic. La posizione dello stack di campioni viene indicata da una freccia di colore nero, o da un accento circonflesso, sopra la sequenza temporale e lo stack di campioni viene visualizzato nella scheda **Corrente**.  
  
 Per visualizzare un profilo di campionamento tradizionale per tutti i segmenti di esecuzione nella visualizzazione corrente, fare clic su **Esecuzione** in Profilo cronologia visibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Rapporto Profilo di esecuzione](../profiling/execution-profile-report.md)   
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)
