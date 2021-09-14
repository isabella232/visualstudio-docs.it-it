---
title: Uso simultaneo di più strumenti del profiler | Microsoft Docs
description: Informazioni su come Profiler prestazioni è stato progettato con l'idea che più strumenti possono essere usati nella stessa sessione per facilitare la comprensione dei problemi di prestazioni.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 5a4c4658282f15b6b34562e51be94d9f2be195a8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710168"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Uso simultaneo di più strumenti del profiler

Il Profiler prestazioni è stato progettato con l'idea che più strumenti possono essere usati nella stessa sessione per facilitare la comprensione dei problemi di prestazioni. La maggior parte degli strumenti Profiler prestazioni supportano l'esecuzione simultanea, ad esempio l'utilizzo [della CPU,](../profiling/cpu-usage.md) [.NET Async e](../profiling/analyze-async.md)lo [strumento Database.](../profiling/analyze-database.md) Per eseguire gli strumenti contemporaneamente nella stessa sessione di diagnostica, fare clic sulla casella di controllo accanto a essi e quindi avviare la sessione di diagnostica.

![Diag Hub All Tools Selected](../profiling/media/diaghuballtoolsselected.png "Diag Hub All Tools Selected")

>[!NOTE]
>Alcuni strumenti, ad esempio lo strumento di allocazione di oggetti [.NET,](../profiling/dotnet-alloc-tool.md) non possono essere eseguiti con altri strumenti a causa del sovraccarico elevato o di altre limitazioni tecniche.

## <a name="time-filtering"></a>Filtro dell'ora 

Durante l'analisi, le operazioni di filtro del tempo vengono applicate tra gli strumenti, pertanto è possibile usare le informazioni in uno strumento per restringere un intervallo di tempo e filtrare i dati in un altro strumento. Questa funzionalità consente di guidare l'analisi in punti specifici di una traccia e di comprendere lo stato dell'applicazione.

![Filtro ora hub diag](../profiling/media/diaghubtimefiltering.png "Filtro ora hub diag")

## <a name="see-also"></a>Vedi anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)
- [Esecuzione degli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods-perf-profiler.md)
