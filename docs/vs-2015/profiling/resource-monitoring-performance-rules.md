---
title: Regole di prestazioni relative al monitoraggio delle risorse | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2bd11b8b18e5dd4e3f6625b1b269d104a6fd5a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530247"
---
# <a name="resource-monitoring-performance-rules"></a>Regole di prestazioni relative al monitoraggio delle risorse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [regole di prestazioni di monitoraggio risorse](https://docs.microsoft.com/visualstudio/profiling/resource-monitoring-performance-rules).  
  
I messaggi relativi alle prestazioni nella categoria Monitoraggio risorse forniscono ulteriori dati sulle prestazioni dell'applicazione. È possibile usare questi dati per analizzare i problemi di prestazioni. Queste regole sono informative e vengono indicate per ogni esecuzione della profilatura.  
  
|||  
|-|-|  
|[DA0501: Consumo medio CPU del processo sottoposto a profilatura.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.|  
|[DA0502: Consumo massimo CPU del processo sottoposto a profilatura](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale massima di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore massimo segnalato fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.|  
|[DA0503: Working set medio in byte del processo sottoposto a profilatura](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria fisica, in byte, usata dal processo mentre era attiva la profilatura. Questa misura della memoria fisica è nota come working set.|  
|[DA0504: Working set massimo in byte del processo sottoposto a profilatura](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria fisica, in byte, usata dal processo mentre era attiva la profilatura.|  
|[DA0505: Byte privati medi allocati per il processo sottoposto a profilatura](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria virtuale che il processo ha allocato in byte mentre era attiva la profilatura. Questa misura della memoria virtuale è nota come *byte privati*. I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.|  
|[DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria virtuale che il processo ha allocato in byte privati mentre era attiva la profilatura.|



