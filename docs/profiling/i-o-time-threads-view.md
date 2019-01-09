---
title: Periodo di I/O (visualizzazione dei thread) | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: cf64339f25e392d4e5790673d77d078b84d02c7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826611"
---
# <a name="io-time-threads-view"></a>Tempo di I/O (visualizzazione thread)
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come I/O. Ciò significa che un thread è in attesa del completamento di un'operazione di I/O. È possibile che il thread sia stato bloccato in un'API oppure da un tempo di attesa del kernel correlato all'I/O che il visualizzatore di concorrenza conteggia come I/O. Le interfacce API `CreateFile()`, `ReadFile()` e `WSARecv()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)