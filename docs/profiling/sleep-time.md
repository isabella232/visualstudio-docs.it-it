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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637685"
---
# <a name="sleep-time"></a>Periodo di sospensione
Questi segmenti nella sequenza temporale sono associati al periodo di blocco categorizzato come Sospensione. La categoria sospensione implica che un thread ha volontariamente abbandonato il core logico e non è in funzione. Durante questo periodo, un thread è stato bloccato in un'API che il visualizzatore di concorrenza conteggia come sospensione. Le interfacce API come `Sleep()` e `SwitchToThread()` rientrano in questo gruppo.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)