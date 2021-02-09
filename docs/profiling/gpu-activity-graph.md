---
title: Grafico Attività GPU | Microsoft Docs
description: Informazioni sul grafico delle attività GPU, che consente di visualizzare nel Visualizzatore di concorrenza il livello di attività DirectX nel sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46f3e4ce7f155679bc3c701af90ff51e0fb20239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907274"
---
# <a name="gpu-activity-graph"></a>Grafico Attività GPU
Il grafico Attività GPU nel visualizzatore di concorrenza visualizza il livello di attività di DirectX nel sistema, misurato in base al numero dei motori di DirectX usati nel tempo.  Il grafico non mostra gli specifici motori usati.  Un motore viene considerato in uso se sta elaborando una qualsiasi operazione GPU.

## <a name="gpu-activity-graph-colors"></a>Colori del grafico Attività GPU
 Il verde indica l'uso dei motori di DirectX da parte del processo corrente.

 Il grigio chiaro indica l'uso dei motori di DirectX da parte di altri processi nel sistema. Per ridurre l'uso dei motori di DirectX da parte di altri processi, ridurre il numero di altri processi in esecuzione nel sistema.

 Il bianco indica la disponibilità dei motori inutilizzati di DirectX nel sistema. Tali motori sono disponibili per il processo se è possibile trovare ulteriori opportunità per sfruttarli. Alcuni motori possono essere usati solo per tipi specifici di attività.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Uso](../profiling/utilization-view.md)