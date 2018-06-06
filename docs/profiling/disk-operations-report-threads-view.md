---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: d145b57b2cacce68b609ddc7aea5cef41cf69762
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764618"
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