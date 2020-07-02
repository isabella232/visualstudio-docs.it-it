---
title: Regole di prestazioni relative al monitoraggio delle risorse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 39df18811a47dfb41c17333121cd9a23d8f46940
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544534"
---
# <a name="resource-monitoring-performance-rules"></a>Regole di prestazioni relative al monitoraggio delle risorse
I messaggi relativi alle prestazioni nella categoria Monitoraggio risorse forniscono ulteriori dati sulle prestazioni dell'applicazione. È possibile usare questi dati per analizzare i problemi di prestazioni. Queste regole sono informative e vengono indicate per ogni esecuzione della profilatura.

|Regola|Descrizione|
|-|-|
|[DA0501: utilizzo medio della CPU da parte del processo sottofilato.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore medio fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.|
|[DA0502: Consumo massimo CPU del processo sottoposto a profilatura](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|In questo messaggio viene indicata la percentuale massima di tempo impiegato da un processore per l'esecuzione di istruzioni dall'applicazione. Il valore indicato è il valore massimo segnalato fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.|
|[DA0503: Working set medio in byte del processo sottoposto a profilatura](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria fisica, in byte, usata dal processo mentre era attiva la profilatura. Questa misura della memoria fisica è nota come working set.|
|[DA0504: Working set massimo in byte del processo sottoposto a profilatura](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria fisica, in byte, usata dal processo mentre era attiva la profilatura.|
|[DA0505: Byte privati medi allocati per il processo sottoposto a profilatura](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità media di memoria virtuale che il processo ha allocato in byte mentre era attiva la profilatura. Questa misura della memoria virtuale è nota come *byte privati*. I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.|
|[DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Questo messaggio indica la quantità massima di memoria virtuale che il processo ha allocato in byte privati mentre era attiva la profilatura.|
