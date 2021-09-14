---
title: Periodo di sincronizzazione | Microsoft Docs
description: Informazioni su come i segmenti nella sequenza temporale sono associati ai tempi di blocco classificati come Sincronizzazione.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 118fa48f6c818c366d733fc29fbcc4a12883a6c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634332"
---
# <a name="synchronization-time"></a>Periodo di sincronizzazione
Questi segmenti nella sequenza temporale sono associati ai periodi di blocco categorizzati come Sincronizzazione. Quando un thread viene contrassegnato come bloccato durante la sincronizzazione, è implicita una delle cause seguenti:

- L'esecuzione del thread potrebbe aver causato una chiamata a un'API di sincronizzazione dei thread nota, come `EnterCriticalSection()` o `WaitForSingleObject()`.

- L'algoritmo di corrispondenza delle API non può essere del tutto completo e pertanto alcune API che potrebbero essere mappate ad altre categorie possono comparire anche nella categoria Sincronizzazione perché un frame nello stack di chiamate raggiunge una primitiva di blocco del kernel sottostante mappata a questa categoria.

  Per comprendere la causa sottostante a un evento di blocco del thread, esaminare attentamente gli stack di chiamate all'origine del blocco e i report di profilatura.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)