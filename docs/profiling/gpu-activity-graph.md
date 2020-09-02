---
title: Grafico Attività GPU | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5734b9eb1b4307f7c32dcb8a170f7c6c571f46ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969566"
---
# <a name="gpu-activity-graph"></a>Grafico Attività GPU
Il grafico Attività GPU nel visualizzatore di concorrenza visualizza il livello di attività di DirectX nel sistema, misurato in base al numero dei motori di DirectX usati nel tempo.  Il grafico non mostra gli specifici motori usati.  Un motore viene considerato in uso se sta elaborando una qualsiasi operazione GPU.

## <a name="gpu-activity-graph-colors"></a>Colori del grafico Attività GPU
 Il verde indica l'uso dei motori di DirectX da parte del processo corrente.

 Il grigio chiaro indica l'uso dei motori di DirectX da parte di altri processi nel sistema. Per ridurre l'uso dei motori di DirectX da parte di altri processi, ridurre il numero di altri processi in esecuzione nel sistema.

 Il bianco indica la disponibilità dei motori inutilizzati di DirectX nel sistema. Tali motori sono disponibili per il processo se è possibile trovare ulteriori opportunità per sfruttarli. Alcuni motori possono essere usati solo per tipi specifici di attività.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Uso](../profiling/utilization-view.md)