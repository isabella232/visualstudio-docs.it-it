---
title: Periodo di sospensione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53f9137c35bd89e812f1d671e2e51f88b343753c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920258"
---
# <a name="sleep-time"></a>Periodo di sospensione
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Sospensione. La categoria sospensione implica che un thread ha volontariamente abbandonato il core logico e non è in funzione. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come sospensione. Le interfacce API come `Sleep()` e `SwitchToThread()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)