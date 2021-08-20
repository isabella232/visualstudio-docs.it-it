---
title: Informazioni sui metodi di raccolta delle prestazioni | Microsoft Docs
description: Informazioni sui diversi scenari in cui la raccolta di dati con un metodo specifico potrebbe essere appropriata.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2949dcb0c7a1343a066599fa6c1950bc757aea2f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140889"
---
# <a name="understand-performance-collection-methods"></a>Informazioni sui metodi di raccolta delle prestazioni

Visual Studio Gli strumenti di profilatura forniscono cinque metodi per la raccolta dei dati sulle prestazioni. Questo articolo descrive i diversi metodi e suggerisce scenari in cui la raccolta di dati con un metodo specifico potrebbe essere appropriata.

> [!NOTE]
> Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative nel modo in cui il profiler Visual Studio raccoglie i dati in queste piattaforme. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni Windows 8 e Windows Server 2012 applicazioni](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Metodo|Descrizione|
|------------|-----------------|
|[Campionamento](#sampling)|Raccoglie dati statistici sul lavoro eseguito da un'app.|
|[Strumentazione](#instrumentation)|Raccoglie informazioni dettagliate sugli intervalli per ogni chiamata di funzione.|
|[Concorrenza](#concurrency)|Raccoglie informazioni dettagliate sulle app multithreading.|
|[Memoria .NET](#net-memory)|Raccoglie informazioni dettagliate sull'allocazione e la Garbage Collection della memoria .NET.|
|[Interazione tra livelli](#tier-interaction)|Raccoglie informazioni sulle chiamate di funzione ADO.NET sincrone a un database SQL Server dati.<br /><br /> Qualsiasi edizione di Visual Studio raccogliere dati del profilo di interazione tra livelli. Tuttavia, è possibile visualizzare i dati solo in Visual Studio Enterprise.|

Usando alcuni dei metodi di profilatura, è anche possibile raccogliere dati aggiuntivi come i contatori delle prestazioni software e hardware. Per altre informazioni, vedere [Raccogliere dati aggiuntivi relativi alle prestazioni](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>campionamento

Il metodo di profilatura del campionamento raccoglie dati statistici sul lavoro eseguito da un'app durante un'esecuzione della profilatura. Il metodo di campionamento è leggero e ha poco effetto sull'esecuzione dei metodi dell'app.

Il campionamento è il metodo predefinito degli strumenti Visual Studio profiling. È utile per le attività seguenti:

- Esplorazioni iniziali delle prestazioni dell'app
- Analisi dei problemi di prestazioni che comportano l'utilizzo del microprocessore (CPU)

Il metodo di profilatura del campionamento interrompe la CPU del computer a intervalli impostati e raccoglie lo stack di chiamate di funzione. I conteggi esclusivi dei campioni vengono incrementati per la funzione in esecuzione. I conteggi inclusivi vengono incrementati per tutte le funzioni chiamanti nello stack di chiamate. I report di campionamento presentano i totali di questi conteggi per i moduli profilati, le funzioni, le righe di codice sorgente e le istruzioni.

Per impostazione predefinita, il profiler imposta l'intervallo di campionamento sui cicli della CPU. È possibile modificare il tipo di intervallo in un altro contatore delle prestazioni cpu o impostare il numero di eventi del contatore per l'intervallo. È anche possibile raccogliere dati di profilatura dell'interazione tra livelli (TIP). Questi dati forniscono informazioni sulle query eseguite a un database SQL Server tramite ADO.NET.

[Raccogliere le statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)

[Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Strumentazione

Il metodo di profilatura della strumentazione raccoglie tempi dettagliati per le chiamate di funzione in un'app profilata. La profilatura della strumentazione è utile per queste attività:

- Analisi dei colli di bottiglia di input/output, ad esempio I/O su disco
- Esame approfondito di un modulo o di un set di funzioni specifico

Il metodo di strumentazione inserisce il codice in un file binario. Il codice acquisisce le informazioni di temporizzazione per tutte le funzioni nel file instrumentato e ogni funzione chiama tali funzioni. La strumentazione identifica anche quando una funzione chiama nel sistema operativo per operazioni come la scrittura in un file.

I report di strumentazione usano questi quattro valori per rappresentare il tempo totale impiegato in una funzione o in una riga di codice sorgente:

- Inclusivo trascorso: tempo totale impiegato per l'esecuzione della funzione o della riga del codice sorgente.

- Inclusivo dell'applicazione: tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente. Le chiamate al sistema operativo vengono escluse.

- Esclusivo trascorso: tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente. Le chiamate ad altre funzioni sono escluse.

- Esclusivo dell'applicazione: tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente. Le chiamate al sistema operativo o ad altre funzioni sono escluse.

È anche possibile raccogliere contatori delle prestazioni cpu e software usando il metodo di strumentazione.

[Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)

[Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Concorrenza

La profilatura della concorrenza raccoglie informazioni sulle app multithreading. La profilatura delle richieste di risorse raccoglie informazioni dettagliate sullo stack di chiamate ogni volta che i thread concorrenti attendono l'accesso a una risorsa condivisa. La visualizzazione della concorrenza raccoglie anche informazioni più generali sull'interazione dell'app multithreading con:

- sé stesso.
- Hardware.
- Sistema operativo.
- Altri processi nel computer host.

I report sulle richieste di risorse visualizzano il numero totale di richieste. Segnalano anche il tempo totale di attesa di una risorsa da parte di moduli, funzioni, righe di codice sorgente e istruzioni. I grafici della sequenza temporale mostrano i contenuti non appena si sono verificati.

Il visualizzatore di concorrenza visualizza informazioni grafiche che consentono di individuare:

- Colli di bottiglia delle prestazioni.
- Sottoutilizzo della CPU.
- L'insoddamento dei thread.
- Migrazione di thread.
- Ritardi di sincronizzazione.
- Aree di I/O sovrapposte.

  Quando possibile, l'output grafico si collega ai dati dello stack di chiamate e del codice sorgente. I dati di visualizzazione della concorrenza possono essere raccolti solo per le app da riga di comando e Windows app.

[Informazioni sui valori dei dati su conflitti di risorse](../profiling/understanding-resource-contention-data-values.md)

[Raccogliere dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)

[Visualizzazioni dei dati relativi ai dati relativi ai consi glio risorse](../profiling/resource-contention-data-views.md)

[Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Memoria .NET

Il metodo di profilatura per l'allocazione di memoria .NET interrompe la CPU a ogni allocazione di un .NET Framework in un'app profilata. Quando il profiler raccoglie anche dati sulla durata degli oggetti, interrompe la CPU dopo ogni .NET Framework Garbage Collection.

Il profiler raccoglie informazioni sul tipo, sulle dimensioni e sul numero di oggetti creati in un'allocazione o distrutti in Garbage Collection.

- Quando si verifica un evento di allocazione, il profiler raccoglie informazioni aggiuntive sullo stack di chiamate della funzione. Il profiler incrementa i conteggi di allocazione esclusivi per la funzione attualmente in esecuzione. Incrementa anche i conteggi inclusivi per tutte le funzioni chiamanti nello stack di chiamate. I report .NET presentano i totali di questi conteggi per i tipi profilati, i moduli, le funzioni, le righe di codice sorgente e le istruzioni.

- Quando si verifica l'operazione di Garbage Collection, il profiler raccoglie i dati sugli oggetti distrutti e sugli oggetti in ogni generazione di Garbage Collection. Al termine dell'esecuzione della profilatura, il profiler registra i dati sugli oggetti che non sono stati eliminati in modo esplicito. Il report Durata oggetto visualizza i totali per ogni tipo allocato nell'esecuzione della profilatura.

È possibile usare la profilatura della memoria .NET in modalità di campionamento o di strumentazione. La modalità selezionata non influisce sui report Allocazione e Durata oggetti univoci per la profilatura della memoria .NET.

- Quando si esegue la profilatura della memoria .NET in modalità di campionamento, il profiler usa gli eventi di allocazione della memoria come intervallo. Viene inoltre visualizzato il numero totale di oggetti e byte allocati come valori inclusivi ed esclusivi nei report.

- Quando si esegue la profilatura della memoria .NET in modalità strumentazione, il profiler raccoglie informazioni dettagliate sull'intervallo insieme ai valori di allocazione inclusiva ed esclusiva.

[Informazioni sull'allocazione di memoria e sui valori dei dati di durata degli oggetti](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Raccogliere dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interazione tra livelli

La profilatura dell'interazione tra livelli aggiunge informazioni a un file di dati di profilatura sulle chiamate sincrone tra una pagina [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] o un'altra app e un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] database. I dati includono il numero e l'ora delle chiamate e le ore massime e minime. È possibile aggiungere dati di interazione tra livelli ai dati di profilatura raccolti con il campionamento, la strumentazione, la memoria .NET o i metodi di concorrenza.

![Flusso di dati di profilatura interazione tra livelli](../profiling/media/tierinteraction_profilingtools.png "Flusso di dati di profilatura interazione tra livelli")

Per informazioni sui dati di interazione tra livelli raccolti dagli strumenti di profilatura, vedere gli articoli seguenti.

[Raccogliere dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)

[Visualizzazioni di interazione tra livelli](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Vedi anche

[Procedura: Raccogliere dati sulle prestazioni per un sito Web](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)
