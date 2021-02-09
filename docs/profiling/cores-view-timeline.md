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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882895"
---
# <a name="cores-view-timeline"></a>Sequenza temporale della visualizzazione Core
Ogni riga della sequenza temporale rappresenta un core processore logico nel sistema profilato. Per ogni riga, l'asse orizzontale indica quale thread era in esecuzione su un core logico in un determinato momento. È possibile passare il mouse su un colore in una sequenza temporale per restituire una descrizione comando che identifica il thread. Per facilitare l'identificazione del thread, la legenda nella parte inferiore della finestra spiega cosa rappresenta ogni colore. Usare lo strumento Zoom per fare zoom avanti e indietro, facendo clic e trascinando o premendo CTRL e muovendo la rotellina del mouse. Quando si passa dalla visualizzazione Core alla visualizzazione thread la coerenza dello zoom viene mantenuta.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Core](../profiling/cores-view.md)
- [Controllo zoom (visualizzazione thread)](../profiling/zoom-control-threads-view.md)