---
title: Periodo di I/O (visualizzazione dei thread) | Microsoft Docs
description: Informazioni sulle modalità di associazione dei segmenti di tempo di I/O a tempi di blocco categorizzati come I/O, il che significa che un thread è in attesa del completamento di un'operazione di I/O.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e147d97616f846339dc12e3941f6944f277d8318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906859"
---
# <a name="io-time-threads-view"></a>Tempo di I/O (visualizzazione thread)
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come I/O. Ciò significa che un thread è in attesa del completamento di un'operazione di I/O. È possibile che il thread sia stato bloccato in un'API oppure da un tempo di attesa del kernel correlato all'I/O che il visualizzatore di concorrenza conteggia come I/O. Le interfacce API `CreateFile()`, `ReadFile()` e `WSARecv()` rientrano in questo gruppo.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)