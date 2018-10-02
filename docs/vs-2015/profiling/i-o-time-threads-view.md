---
title: Periodo di I/O (visualizzazione dei thread) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25512da43fc32b42c2a1f79e3c8dbe992ea30ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533028"
---
# <a name="io-time-threads-view"></a>Tempo di I/O (visualizzazione Thread)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [I / O (visualizzazione thread) ora](https://docs.microsoft.com/visualstudio/profiling/i-o-time-threads-view).  
  
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come I/O. Ciò significa che un thread è in attesa del completamento di un'operazione di I/O. È possibile che il thread sia stato bloccato in un'API oppure da un tempo di attesa del kernel correlato all'I/O che il visualizzatore di concorrenza conteggia come I/O. Le interfacce API `CreateFile()`, `ReadFile()` e `WSARecv()` rientrano in questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)



