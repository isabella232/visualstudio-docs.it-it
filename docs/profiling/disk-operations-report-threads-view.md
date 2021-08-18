---
title: Rapporto delle operazioni su disco (visualizzazione thread) | Microsoft Docs
description: Nel rapporto delle operazioni su disco vengono descritte le operazioni I/O eseguite nei canali del disco. Vedere le informazioni segnalate per ogni accesso al disco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ff9790ab1178ecae056c4af0fcea673e8e94ead7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142026"
---
# <a name="disk-operations-report-threads-view"></a>Report delle operazioni su disco (visualizzazione Thread)
Nel rapporto delle operazioni su disco vengono descritte le operazioni I/O eseguite nei canali del disco.

 Per ogni accesso al disco che avviene per conto del processo sottoposto a profilatura nell'intervallo di tempo attualmente visibile, vengono segnalate le informazioni seguenti:

- Nome e PID del processo che ha eseguito l'accesso al disco

- ID del thread che ha eseguito l'accesso al disco

- Nome del file al quale è stato eseguito l'accesso.

- Numero di letture per ogni file

- Numero di byte letti.

- Latenza di lettura in millisecondi

- Numero di operazioni di scrittura

- Numero di byte scritti

- Latenza di scrittura in millisecondi

## <a name="see-also"></a>Vedi anche
- [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)