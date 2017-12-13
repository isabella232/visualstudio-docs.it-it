---
title: Periodo di sospensione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.sleep
helpviewer_keywords: Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52ce4aa37b607072a0cf91c4baf0dbe6b077ac5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="sleep-time"></a>Periodo di sospensione
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Sospensione. La categoria sospensione implica che un thread ha volontariamente abbandonato il core logico e non è in funzione. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come sospensione. Le interfacce API come `Sleep()` e `SwitchToThread()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Threads View](../profiling/threads-view-parallel-performance.md) (Visualizzazione thread)