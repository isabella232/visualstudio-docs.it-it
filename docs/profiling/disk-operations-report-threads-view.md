---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95173f260ce8ed40c607c7026df727267dd3866e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955266"
---
# <a name="disk-operations-report-threads-view"></a>Report delle operazioni su disco (visualizzazione Thread)
Nel rapporto delle operazioni su disco vengono descritte le operazioni I/O eseguite nei canali del disco.  
  
 Per ogni accesso al disco che avviene per conto del processo sottoposto a profilatura nell'intervallo di tempo attualmente visibile, vengono segnalate le informazioni seguenti:  
  
-   Nome e PID del processo che ha eseguito l'accesso al disco  
  
-   ID del thread che ha eseguito l'accesso al disco  
  
-   Nome del file al quale è stato eseguito l'accesso.  
  
-   Numero di letture per ogni file  
  
-   Numero di byte letti.  
  
-   Latenza di lettura in millisecondi  
  
-   Numero di operazioni di scrittura  
  
-   Numero di byte scritti  
  
-   Latenza di scrittura in millisecondi  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)