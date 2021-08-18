---
title: Regole di prestazioni relative al monitoraggio delle risorse | Microsoft Docs
description: Informazioni su come i messaggi sulle prestazioni nella categoria Monitoraggio risorse forniscono dati aggiuntivi sulle prestazioni dell'applicazione.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dcae9f26bd87192a2388eaf3403fdec39e210331d98f2b1f55340cf2f6dbbf04
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442021"
---
# <a name="resource-monitoring-performance-rules"></a>Regole di prestazioni relative al monitoraggio delle risorse
I messaggi relativi alle prestazioni nella categoria Monitoraggio risorse forniscono ulteriori dati sulle prestazioni dell'applicazione. È possibile usare questi dati per analizzare i problemi di prestazioni. Queste regole sono informative e vengono indicate per ogni esecuzione della profilatura.

|Regola|Descrizione|
|-|-|
|[DA0501: utilizzo medio della CPU del processo profilato.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.|
|[DA0502: Consumo massimo CPU del processo sottoposto a profilatura](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale massima di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore massimo segnalato fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.|
|[DA0503: Working set medio in byte del processo sottoposto a profilatura](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria fisica, in byte, usata dal processo mentre era attiva la profilatura. Questa misura della memoria fisica è nota come working set.|
|[DA0504: Working set massimo in byte del processo sottoposto a profilatura](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria fisica, in byte, usata dal processo mentre era attiva la profilatura.|
|[DA0505: Byte privati medi allocati per il processo sottoposto a profilatura](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria virtuale che il processo ha allocato in byte mentre era attiva la profilatura. Questa misura della memoria virtuale è nota come *byte privati*. I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.|
|[DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria virtuale che il processo ha allocato in byte privati mentre era attiva la profilatura.|
