---
title: Tempo di gestione della memoria | Microsoft Docs
description: Informazioni su come questo scenario implica che un thread viene bloccato da un evento associato a un'operazione di gestione della memoria, ad esempio il paging.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ed5483c89e9435d5bd0712ef562e80fde2c73e26
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637083"
---
# <a name="memory-management-time"></a>Tempo di gestione della memoria
Questi segmenti nella sequenza temporale sono associati a tempi di blocco categorizzati come gestione della memoria. Questo scenario implica che un thread è bloccato da un evento associato a un'operazione di gestione della memoria quale il paging. Durante questo periodo, un thread è stato bloccato in un'API o in uno stato del kernel che il visualizzatore di concorrenza calcola come gestione della memoria. Si tratta di eventi come il paging e l'allocazione di memoria.

 Esaminare gli stack di chiamate e i rapporti di profilo associati per comprendere meglio i motivi alla base della categorizzazione dei blocchi come gestione della memoria.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)