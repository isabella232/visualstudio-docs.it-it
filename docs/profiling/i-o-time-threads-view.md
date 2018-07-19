---
title: Periodo di I/O (visualizzazione dei thread) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 253aa8c3a8ca5161fbb95e18f38f0ff232cd37bc
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844846"
---
# <a name="io-time-threads-view"></a>Tempo di I/O (visualizzazione thread)
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come I/O. Ciò significa che un thread è in attesa del completamento di un'operazione di I/O. È possibile che il thread sia stato bloccato in un'API oppure da un tempo di attesa del kernel correlato all'I/O che il visualizzatore di concorrenza conteggia come I/O. Le interfacce API `CreateFile()`, `ReadFile()` e `WSARecv()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)