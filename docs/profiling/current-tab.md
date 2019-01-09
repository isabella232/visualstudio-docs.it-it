---
title: Scheda corrente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04700ebac239be6c72038b30c67d66cfb0e3ec7f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964734"
---
# <a name="current-tab"></a>Scheda Corrente
Facendo clic sulla scheda **Corrente**, è possibile visualizzare uno stack di chiamate (se disponibile) che è più vicino al punto di selezione corrente nella sequenza temporale se è selezionato un segmento di thread della CPU.  In questo caso, il punto di selezione è rappresentato da una freccia nera (o punto di inserimento) sopra la sequenza temporale. Quando viene selezionato un segmento di blocco, il punto di inserimento non viene visualizzato perché non è in esecuzione. Tuttavia, il segmento è ancora evidenziato e viene visualizzato uno stack di chiamate.  
  
 La scheda **Corrente** visualizza anche informazioni sui segmenti di attività di DirectX, marcatori e accesso I/O.  Per i segmenti di attività di DirectX, vengono visualizzate le informazioni sul modo in cui vengono elaborati i pacchetti DMA dalla coda di hardware.  Per i marcatori, vengono visualizzate informazioni sul tipo di marcatore e descrizione.  Per l'accesso I/O, vengono visualizzate informazioni sui file e sul numero di byte letti o scritti.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)