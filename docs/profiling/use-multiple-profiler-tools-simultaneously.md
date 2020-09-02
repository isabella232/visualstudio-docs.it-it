---
title: Uso simultaneo di più strumenti Profiler | Microsoft Docs
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f72757d46496c3990c0a0d4205753d185078eac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85332033"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Uso simultaneo di più strumenti del profiler

Il profiler delle prestazioni è stato progettato con l'idea che è possibile usare più strumenti nella stessa sessione per facilitare la comprensione dei problemi di prestazioni. La maggior parte degli strumenti nel profiler delle prestazioni supporta l'esecuzione simultanea, ad esempio l' [utilizzo della CPU](../profiling/cpu-usage.md), [lo strumento asincrono .NET](../profiling/analyze-async.md)e lo strumento di [database](../profiling/analyze-database.md) . Per eseguire gli strumenti simultaneamente nella stessa sessione di diagnostica, fare clic sulla casella di controllo accanto a essi, quindi avviare la sessione di diagnostica.

![Hub diag-tutti gli strumenti selezionati](../profiling/media/diaghuballtoolsselected.png "Hub diag-tutti gli strumenti selezionati")

>[!NOTE]
>Alcuni strumenti, ad esempio lo strumento di [allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md) , non possono essere eseguiti con altri strumenti a causa del sovraccarico elevato o di altre limitazioni tecniche.

## <a name="time-filtering"></a>Filtro temporale 

Durante l'analisi, le operazioni di filtro del tempo vengono applicate tra gli strumenti, pertanto è possibile utilizzare le informazioni in uno strumento per limitare un intervallo di tempo e filtrare i dati in un altro strumento. Questa funzionalità consente di eseguire l'analisi su punti specifici in una traccia e di comprendere lo stato dell'applicazione.

![Filtro tempo Hub diag](../profiling/media/diaghubtimefiltering.png "Filtro tempo Hub diag")

## <a name="see-also"></a>Vedere anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)
- [Esecuzione di strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods-perf-profiler.md)
