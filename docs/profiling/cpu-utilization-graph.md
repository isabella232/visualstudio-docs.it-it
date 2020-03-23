---
title: Grafico di utilizzo della CPU | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e09526930bf98141ae4f9d4d204b20383763c208
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552876"
---
# <a name="cpu-utilization-graph"></a>Grafico di utilizzo della CPU
Il grafico di utilizzo della CPU visualizza il livello di utilizzo in un'app nel tempo. L'asse X rappresenta la durata della traccia e l'asse Y rappresenta il numero di core logici nel sistema. Il grafico non indica quale core specifico è attivo in un momento determinato. Ad esempio, se due core sono in esecuzione al 50% per un determinato periodo di tempo, il grafico indica che viene usato un solo core logico.

## <a name="cpu-utilization-graph-colors"></a>Colori del grafico di utilizzo della CPU

- Il colore verde indica l'utilizzo dei core logici del sistema da parte del processo corrente.

- Il colore grigio chiaro indica l'utilizzo dei core logici da parte di altri processi nel sistema. Una percentuale elevata di colore grigio chiaro nel grafico della CPU indica che il sistema è eccessivamente caricato da altri processi e che il processo in corso potrebbe essere annullato dagli altri processi. Per ridurre l'uso dei core logici da parte di altri processi, ridurre il numero di tali processi eseguiti nel sistema.

- Il colore grigio scuro indica il consumo di core logici da parte del processo di sistema. Non è possibile controllare direttamente questa attività, ma è utile essere al corrente di questi eventi perché possono incidere sulla disponibilità di core logici per il processo.

- Il colore bianco indica la disponibilità di core logici non usati nel sistema. Tali core sono disponibili per il processo se è possibile trovare altre opportunità di parallelismo.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Uso](../profiling/utilization-view.md)
- [Utilizzo CPU medio](../profiling/average-cpu-utilization.md)