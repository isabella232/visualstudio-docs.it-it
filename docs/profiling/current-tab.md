---
title: Scheda corrente | Microsoft Docs
description: Selezionare la scheda corrente della visualizzazione thread per visualizzare uno stack di chiamate per un segmento di thread della CPU o un segmento di blocco. Sono inoltre disponibili informazioni sui segmenti DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4125a40ea0be18cceb99e7f3a8118a10d26a5437
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955866"
---
# <a name="current-tab"></a>Scheda Corrente
Facendo clic sulla scheda **Corrente**, è possibile visualizzare uno stack di chiamate (se disponibile) che è più vicino al punto di selezione corrente nella sequenza temporale se è selezionato un segmento di thread della CPU.  In questo caso, il punto di selezione è rappresentato da una freccia nera (o punto di inserimento) sopra la sequenza temporale. Quando viene selezionato un segmento di blocco, il punto di inserimento non viene visualizzato perché non è in esecuzione. Tuttavia, il segmento è ancora evidenziato e viene visualizzato uno stack di chiamate.

 La scheda **Corrente** visualizza anche informazioni sui segmenti di attività di DirectX, marcatori e accesso I/O.  Per i segmenti di attività di DirectX, vengono visualizzate le informazioni sul modo in cui vengono elaborati i pacchetti DMA dalla coda di hardware.  Per i marcatori, vengono visualizzate informazioni sul tipo di marcatore e descrizione.  Per l'accesso I/O, vengono visualizzate informazioni sui file e sul numero di byte letti o scritti.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)