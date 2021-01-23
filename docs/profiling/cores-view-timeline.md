---
title: Sequenza temporale della visualizzazione Core | Microsoft Docs
description: 'Informazioni sulle nozioni di base della sequenza temporale: come determinare il thread in cui è stato eseguito in qualsiasi momento e come eseguire lo zoom avanti e indietro.'
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64012be03c08f3737f4e57a05217bf46082daeb6
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720748"
---
# <a name="cores-view-timeline"></a>Sequenza temporale della visualizzazione Core
Ogni riga della sequenza temporale rappresenta un core processore logico nel sistema profilato. Per ogni riga, l'asse orizzontale indica quale thread era in esecuzione su un core logico in un determinato momento. È possibile passare il mouse su un colore in una sequenza temporale per restituire una descrizione comando che identifica il thread. Per facilitare l'identificazione del thread, la legenda nella parte inferiore della finestra spiega cosa rappresenta ogni colore. Usare lo strumento Zoom per fare zoom avanti e indietro, facendo clic e trascinando o premendo CTRL e muovendo la rotellina del mouse. Quando si passa dalla visualizzazione Core alla visualizzazione thread la coerenza dello zoom viene mantenuta.

## <a name="see-also"></a>Vedere anche
- [Visualizzazione Core](../profiling/cores-view.md)
- [Controllo zoom (visualizzazione thread)](../profiling/zoom-control-threads-view.md)