---
title: Ottimizzazione delle impostazioni del profiler | Microsoft Docs
description: Informazioni su come Profiler prestazioni e Strumenti di diagnostica finestra di dialogo in Visual Studio hanno molte impostazioni diverse che influiscono sulle prestazioni complessive degli strumenti.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 482ee640f4b84348e00f2f3da42a4dbe13f73460
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710184"
---
# <a name="optimizing-profiler-settings"></a>Ottimizzazione delle impostazioni del profiler

La Profiler prestazioni e Strumenti di diagnostica in Visual Studio hanno molte impostazioni diverse che influiscono sulle prestazioni complessive degli strumenti. La modifica di alcune impostazioni può causare l'esecuzione rapida dell'analisi o tempi di attesa aggiuntivi durante l'elaborazione dei risultati negli strumenti. Di seguito è riportato un riepilogo di determinate impostazioni e del relativo impatto sulle prestazioni.

## <a name="symbol-settings"></a>Impostazioni simboli

Le impostazioni dei simboli disponibili nelle opzioni del debugger ( Opzioni > di debug **>** Simboli o Strumenti > Opzioni > Debug **> Simboli**) hanno un impatto significativo sul tempo necessario per generare i risultati negli strumenti. Se si abilitano i server di simboli **o _NT_SYMBOL_PATH** il profiler richiede i simboli per ogni modulo caricato in un report. Attualmente, il profiler carica sempre automaticamente tutti i simboli indipendentemente dalla preferenza di caricamento automatico dei simboli.

![Pagina di caricamento dei simboli](../profiling/media/symbolloading.png "Caricamento dei simboli")

Lo stato di avanzamento del caricamento dei simboli è visibile nella **finestra Output** sotto l'intestazione **Strumenti di diagnostica** simboli.

![Avanzamento del caricamento dei simboli](../profiling/media/symbolloadingprogress.png "Avanzamento del caricamento dei simboli")

Dopo il download, i simboli vengono memorizzati nella cache, che velocizza l'analisi futura, ma richiede comunque il caricamento e l'analisi dei file. Se il caricamento dei simboli rallenta l'analisi, provare a disattivare i server di simboli e cancellare la cache dei simboli. Basarsi invece sui simboli compilati in locale per il progetto.

## <a name="show-external-code"></a>Mostra codice esterno

Molti degli strumenti all'interno **della finestra Profiler prestazioni** e **Strumenti di diagnostica** hanno un concetto di codice utente e codice esterno. Il codice utente è qualsiasi codice compilato dalla soluzione aperta o dall'area di lavoro aperta. Il codice esterno è qualsiasi altro elemento. Mantenendo disabilitata l'impostazione Mostra  codice esterno o Mostra solo il codice, è possibile consentire agli strumenti di aggregare il codice esterno in un singolo frame di primo livello, riducendo notevolmente la quantità di elaborazione necessaria per visualizzare i risultati.  In questo modo gli utenti possono vedere ciò che è stato chiamato nel codice esterno che ha creato il rallentamento mantenendo al minimo i dati da elaborare. Quando possibile, lasciare **disabilitato Mostra** codice esterno e assicurarsi che la soluzione o l'area di lavoro sia aperta per la diagsession che si sta analizzando.

## <a name="trace-duration"></a>Durata traccia

La profilatura di durate più piccole comporta un minor numero di dati, che è più veloce da analizzare. In genere è consigliabile provare a limitare le tracce a non più di cinque minuti di dati sulle prestazioni. Alcuni strumenti, ad esempio lo strumento Utilizzo [CPU,](../profiling/cpu-usage.md) consentono di sospendere la raccolta dei dati durante l'esecuzione dello strumento, in modo da limitare la quantità di dati raccolti allo scenario che si è interessati ad analizzare.

## <a name="sampling-frequency"></a>Frequenza di campionamento

Alcuni strumenti, ad esempio lo strumento [Utilizzo CPU](../profiling/cpu-usage.md) e lo strumento Allocazione oggetti [NET,](../profiling/dotnet-alloc-tool.md) consentono di regolare una frequenza di campionamento. L'aumento di questa frequenza di campionamento consente di misurare in modo più preciso, ma aumenta la quantità di dati generati. In genere, è meglio lasciare questa impostazione alla frequenza predefinita, a meno che non venga analizzato un problema specifico.

![Pagina delle proprietà dell'hub Diag](../profiling/media/diaghubpropertiespage.png "Pagina delle proprietà dell'hub Diag")

## <a name="see-also"></a>Vedi anche

- [Esecuzione degli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Uso simultaneo di più strumenti del profiler](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods-perf-profiler.md)
