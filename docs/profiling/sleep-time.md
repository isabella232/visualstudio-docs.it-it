---
title: Periodo di sospensione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: b94b1695eb36aa8f55847c21a14d72357d51a405
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35668894"
---
# <a name="sleep-time"></a>Periodo di sospensione
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Sospensione. La categoria sospensione implica che un thread ha volontariamente abbandonato il core logico e non è in funzione. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come sospensione. Le interfacce API come `Sleep()` e `SwitchToThread()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)