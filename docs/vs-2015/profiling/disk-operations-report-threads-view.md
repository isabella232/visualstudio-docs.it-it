---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
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
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe16116131c1ed6d0233abbd2e0480946b5a5423
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520191"
---
# <a name="disk-operations-report-threads-view"></a>Report delle operazioni su disco (visualizzazione Thread)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [rapporto delle operazioni su disco (visualizzazione thread)](https://docs.microsoft.com/visualstudio/profiling/disk-operations-report-threads-view).  
  
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



