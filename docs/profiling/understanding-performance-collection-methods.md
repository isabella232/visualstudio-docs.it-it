---
title: Informazioni sui metodi di raccolta delle prestazioni | Microsoft Docs
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ecbabae86b762c9143dba6be5aa0e4683a92b0dd
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250768"
---
# <a name="understand-performance-collection-methods"></a>Informazioni sui metodi di raccolta delle prestazioni

Gli strumenti di profilatura di Visual Studio forniscono cinque metodi per la raccolta dei dati sulle prestazioni. Questo articolo descrive i diversi metodi e suggerisce scenari in cui la raccolta di dati con un determinato metodo può essere appropriata.

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative nel modo in cui il profiler di Visual Studio raccoglie i dati su queste piattaforme. Le app della piattaforma UWP richiedono anche nuove tecniche di raccolta. Vedere [strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Metodo|Descrizione|
|------------|-----------------|
|[Campionamento](#sampling)|Raccoglie i dati statistici sul lavoro svolto da un'app.|
|[Strumentazione](#instrumentation)|Raccoglie informazioni dettagliate sugli intervalli per ogni chiamata di funzione.|
|[Concorrenza](#concurrency)|Raccoglie informazioni dettagliate sulle app multithread.|
|[Memoria .NET](#net-memory)|Raccoglie informazioni dettagliate sull'allocazione e la Garbage Collection della memoria .NET.|
|[Interazione tra livelli](#tier-interaction)|Raccoglie informazioni sulle chiamate di funzione ADO.NET sincrone a un database SQL Server.<br /><br /> Qualsiasi edizione di Visual Studio è in grado di raccogliere dati del profilo di interazione tra livelli. Tuttavia, è possibile visualizzare i dati solo in Visual Studio Enterprise.|

Utilizzando alcuni dei metodi di profilatura, è anche possibile raccogliere dati aggiuntivi quali i contatori delle prestazioni software e hardware. Per altre informazioni, vedere [Raccogliere dati aggiuntivi relativi alle prestazioni](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>campionamento

Il metodo di profilatura del campionamento raccoglie dati statistici sul lavoro eseguito da un'app durante un'esecuzione della profilatura. Il metodo di campionamento è leggero e ha un effetto minimo sull'esecuzione dei metodi dell'app.

Il campionamento è il metodo predefinito per gli strumenti di profilatura di Visual Studio. È utile per le attività seguenti:

- Esplorazione iniziale delle prestazioni dell'app
- Analisi dei problemi di prestazioni che coinvolgono l'utilizzo del microprocessore (CPU)

Il metodo di profilatura del campionamento interrompe la CPU del computer a intervalli prestabiliti e raccoglie lo stack di chiamate della funzione. I conteggi dei campioni esclusivi vengono incrementati per la funzione in esecuzione. I conteggi inclusivi vengono incrementati per tutte le funzioni chiamante nello stack di chiamate. I report di campionamento presentano i totali di questi conteggi per i moduli, le funzioni, le righe del codice sorgente e le istruzioni profilate.

Per impostazione predefinita, il profiler imposta l'intervallo di campionamento sui cicli della CPU. È possibile modificare il tipo di intervallo in un altro contatore delle prestazioni della CPU o impostare il numero di eventi del contatore per l'intervallo. È anche possibile raccogliere dati di profilatura dell'interazione tra livelli (TIP). Questi dati forniscono informazioni sulle query eseguite in un database di SQL Server tramite ADO.NET.

[Raccogliere le statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)

[Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>Strumentazione

Il metodo di profilatura della strumentazione raccoglie un intervallo dettagliato per le chiamate di funzione in un'applicazione profilata. La profilatura della strumentazione è utile per le attività seguenti:

- Analisi di colli di bottiglia di input/output, ad esempio I/O su disco
- Chiusura dell'esame di un particolare modulo o set di funzioni

Il metodo di strumentazione inserisce codice in un file binario. Il codice acquisisce le informazioni di temporizzazione per tutte le funzioni nel file instrumentato e ogni funzione chiama tali funzioni. La strumentazione identifica anche quando una funzione chiama il sistema operativo per operazioni come la scrittura in un file.

I report di strumentazione usano questi quattro valori per rappresentare il tempo totale impiegato in una funzione o in una riga del codice sorgente:

- Inclusivo trascorso: tempo totale impiegato per l'esecuzione della funzione o della riga del codice sorgente.

- Inclusivo applicazione-tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente. Le chiamate al sistema operativo sono escluse.

- Tempo esclusivo trascorso: tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente. Le chiamate ad altre funzioni sono escluse.

- Applicazione esclusiva: tempo impiegato per l'esecuzione della funzione o della riga del codice sorgente. Le chiamate al sistema operativo o ad altre funzioni sono escluse.

È anche possibile raccogliere i contatori delle prestazioni della CPU e del software tramite il metodo di strumentazione.

[Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)

[Raccogliere dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Concorrenza

La profilatura della concorrenza raccoglie informazioni sulle app multithread. La profilatura della contesa delle risorse raccoglie informazioni dettagliate sullo stack di chiamate ogni volta che i thread in conflitto attendono l'accesso a una risorsa condivisa. La visualizzazione della concorrenza raccoglie anche informazioni più generali sul modo in cui l'app multithreading interagisce con:

- Stesso.
- L'hardware.
- Sistema operativo.
- Altri processi sul computer host.

Report sui conflitti di risorse Visualizza il numero totale di conflitti. Segnalano inoltre il tempo totale di attesa di una risorsa per i moduli, le funzioni, le righe del codice sorgente e le istruzioni. I grafici della sequenza temporale mostrano i conflitti che si sono verificati.

Il Visualizzatore di concorrenza Visualizza informazioni grafiche che consentono di individuare:

- Colli di bottiglia delle prestazioni.
- Sottoutilizzo della CPU.
- Contesa di thread.
- Migrazione di thread.
- Ritardi di sincronizzazione.
- Aree di I/O sovrapposte.

  Quando possibile, l'output grafico si collega ai dati dallo stack di chiamate e dal codice sorgente. I dati di visualizzazione della concorrenza possono essere raccolti solo per le app della riga di comando e le app di Windows.

[Informazioni sui valori dei dati su conflitti di risorse](../profiling/understanding-resource-contention-data-values.md)

[Raccogliere dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)

[Visualizzazioni dei dati sui conflitti di risorse](../profiling/resource-contention-data-views.md)

[Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>Memoria .NET

Il metodo di profilatura per l'allocazione di memoria .NET interrompe la CPU a ogni allocazione di un oggetto .NET Framework in un'applicazione profilata. Quando il profiler raccoglie anche dati sulla durata degli oggetti, interrompe la CPU dopo ogni .NET Framework Garbage Collection.

Il profiler raccoglie informazioni sul tipo, le dimensioni e il numero di oggetti creati in un'allocazione o eliminati definitivamente in Garbage Collection.

- Quando si verifica un evento di allocazione, il profiler raccoglie informazioni aggiuntive sullo stack di chiamate della funzione. Il profiler incrementa i conteggi delle allocazioni esclusive per la funzione attualmente in esecuzione. Incrementa inoltre i conteggi inclusivi per tutte le funzioni chiamante nello stack di chiamate. I report .NET presentano i totali di questi conteggi per i tipi profilati, i moduli, le funzioni, le righe del codice sorgente e le istruzioni.

- Quando si verifica Garbage Collection, il profiler raccoglie i dati sugli oggetti eliminati e sugli oggetti in ogni generazione di Garbage Collection. Al termine dell'esecuzione della profilatura, il profiler registra i dati sugli oggetti che non sono stati eliminati in modo esplicito. Il report durata oggetti Visualizza i totali per ogni tipo allocato nell'esecuzione della profilatura.

È possibile utilizzare la profilatura della memoria .NET in modalità di campionamento o di strumentazione. La modalità selezionata non influisce sui report di allocazione e durata degli oggetti che sono univoci per la profilatura della memoria .NET.

- Quando si esegue la profilatura della memoria .NET in modalità di campionamento, il profiler utilizza gli eventi di allocazione della memoria come intervallo. Viene inoltre visualizzato il numero totale di oggetti e byte allocati come valori inclusivi ed esclusivi nei report.

- Quando si esegue la profilatura della memoria .NET in modalità di strumentazione, il profiler raccoglie informazioni dettagliate sull'intervallo insieme ai valori di allocazione inclusivi ed esclusivi.

[Informazioni sull'allocazione di memoria e sui valori dei dati di durata degli oggetti](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[Raccogliere dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Interazione tra livelli

La profilatura dell'interazione tra livelli aggiunge informazioni a un file di dati di profilatura sulle chiamate sincrone [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] tra una [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pagina o un'altra app e un [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] database. I dati includono il numero e l'ora delle chiamate e i tempi massimi e minimi. È possibile aggiungere dati di interazione tra livelli ai dati di profilatura raccolti con i metodi di campionamento, strumentazione, memoria .NET o concorrenza.

![Flusso di file di profilatura interazione tra livelli](../profiling/media/tierinteraction_profilingtools.png "Flusso di file di profilatura interazione tra livelli")

Per informazioni sui dati di interazione tra livelli raccolti dagli strumenti di profilatura, vedere gli articoli seguenti.

[Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)

[Viste di interazione tra livelli](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Vedere anche

[Procedura: Raccogliere dati sulle prestazioni per un sito Web](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)
