---
title: Ottimizzazione delle impostazioni del profiler | Microsoft Docs
ms.date: 4/29/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9ff76364026230d08d03c91d14bddba3c325e7be
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290653"
---
# <a name="optimizing-profiler-settings"></a>Ottimizzazione delle impostazioni del profiler

Il profiler delle prestazioni e la finestra Strumenti di diagnostica in Visual Studio hanno molte impostazioni diverse che influiscono sulle prestazioni complessive degli strumenti. La modifica di alcune impostazioni può causare un'esecuzione rapida dell'analisi o causare tempi di attesa aggiuntivi durante l'elaborazione dei risultati negli strumenti. Di seguito è riportato un riepilogo di alcune impostazioni e il relativo effetto sulle prestazioni.

## <a name="symbol-settings"></a>Impostazioni simboli

Le impostazioni dei simboli presenti nelle opzioni del debugger (**Debug > opzioni > simboli**) hanno un impatto significativo sul tempo impiegato per generare i risultati negli strumenti. L'abilitazione dei server di simboli o l'utilizzo della **_NT_SYMBOL_PATH** fa sì che il profiler richieda simboli per ogni modulo caricato in un report. Attualmente, il profiler carica sempre automaticamente tutti i simboli indipendentemente dalle preferenze di caricamento automatico dei simboli.

![Pagina di caricamento dei simboli](../profiling/media/symbolloading.png "Caricamento simboli")

Lo stato di avanzamento del caricamento dei simboli può essere visualizzato nella finestra **output** sotto l'intestazione **strumenti di diagnostica** .

![Stato caricamento simboli](../profiling/media/symbolloadingprogress.png "Stato caricamento simboli")

Al termine del download, i simboli vengono memorizzati nella cache, che accelererà l'analisi futura, ma richiederà comunque il caricamento e l'analisi dei file. Se il caricamento dei simboli rallenta l'analisi, provare a disattivare i server dei simboli e cancellare la cache dei simboli. Al contrario, si basano sui simboli compilati localmente per il progetto.

## <a name="show-external-code"></a>Mostra codice esterno

Molti degli strumenti nel **Profiler delle prestazioni** e nella finestra **strumenti di diagnostica** hanno un concetto di codice utente rispetto al codice esterno. Il codice utente è un codice compilato dall'area di lavoro Apri o Apri soluzione. Il codice esterno è qualsiasi altro elemento. Se l'opzione **Mostra codice esterno** è disabilitata o **Mostra Just My Code** abilitata, gli strumenti consentono di aggregare codice esterno a un singolo frame di primo livello, riducendo notevolmente la quantità di elaborazione necessaria per mostrare i risultati. Ciò consente agli utenti di vedere cosa è stato chiamato in codice esterno che ha creato il rallentamento mantenendo i dati da elaborare come minimo. Quando possibile, lasciare **Mostra codice esterno** disabilitato e assicurarsi che la soluzione o l'area di lavoro sia aperta per il DIAGSESSION che si sta analizzando.

## <a name="trace-duration"></a>Durata della traccia

La profilatura di durate minori comporta un minor numero di dati, che risulta più veloce da analizzare. In genere è consigliabile provare a limitare le tracce a non più di cinque minuti di dati sulle prestazioni. Alcuni strumenti, ad esempio lo strumento [utilizzo CPU](../profiling/cpu-usage.md) , consentono di sospendere la raccolta dei dati durante l'esecuzione dello strumento, in modo che sia possibile limitare la quantità di dati raccolti nello scenario che si desidera analizzare.

## <a name="sampling-frequency"></a>Frequenza di campionamento

Alcuni strumenti, ad esempio lo strumento [utilizzo CPU](../profiling/cpu-usage.md) e lo strumento di [allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md) , consentono di modificare la frequenza di campionamento. L'aumento della frequenza di campionamento consente di misurare più precisamente, ma aumenta la quantità di dati generati. In genere, è preferibile lasciare questa impostazione con la frequenza predefinita, a meno che non venga analizzato un problema specifico.

![Pagina delle proprietà dell'hub diag](../profiling/media/diaghubpropertiespage.png "Pagina delle proprietà dell'hub diag")

## <a name="see-also"></a>Vedi anche

- [Esecuzione di strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Uso simultaneo di più strumenti del profiler](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods-perf-profiler.md)
