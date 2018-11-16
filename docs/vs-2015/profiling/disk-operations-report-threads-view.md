---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e83a471fe451becf445a7d14f2b312fe5a65c38
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801940"
---
# <a name="disk-operations-report-threads-view"></a>Report delle operazioni su disco (visualizzazione Thread)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



