---
title: Introduzione agli strumenti di profilatura
description: Esaminare una breve panoramica dei diversi strumenti di diagnostica disponibili in Visual Studio.
ms.custom: ''
ms.date: 02/18/2021
ms.topic: overview
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 855a04fae1d5b406019e758c6d6f931d6657bb4e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145378"
---
# <a name="first-look-at-profiling-tools"></a>Presentazione degli strumenti di profilatura

Visual Studio offre un'ampia gamma di strumenti di profilatura che consentono di diagnosticare diversi tipi di problemi di prestazioni in base al tipo di app. Questo articolo fornisce una rapida panoramica degli strumenti di profilatura più comuni.

Per visualizzare il supporto dello strumento di profilatura per diversi tipi di app, vedere [quale strumento si deve usare?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Misurare le prestazioni durante il debug

Gli strumenti di profilatura a cui è possibile accedere durante una sessione di debug sono disponibili nella finestra Strumenti di diagnostica. La finestra Strumenti di diagnostica viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare la finestra, fare clic su **Debug/Windows/Mostra strumenti di diagnostica**. Con finestra aperta è possibile selezionare gli strumenti per cui si vogliono raccogliere dati.

![Finestra Strumenti di diagnostica](../profiling/media/prof-tour-diagnostic-tools.png "Strumenti di diagnostica")

Durante il debug è possibile usare la finestra **Strumenti di diagnostica** per l'analisi della CPU e dell'uso della memoria e si possono visualizzare gli eventi che generano informazioni relative alle prestazioni.

![Visualizzazione riepilogo Strumenti di diagnostica](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Riepilogo Strumenti di diagnostica")

La finestra di **strumenti di diagnostica** è un modo comune per profilare le app, ma per le build di rilascio è possibile anche eseguire un'analisi post-mortem dell'app. Per altre informazioni sui diversi approcci, vedere [eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Per visualizzare il supporto dello strumento di profilatura per diversi tipi di app, vedere [quale strumento si deve usare?](#which-tool-should-i-use)

Gli strumenti disponibili nella finestra Strumenti di diagnostica o durante una sessione di debug includono:
- [Utilizzo della CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Utilizzo memoria](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**. È possibile usare gli strumenti [post-mortem](#post_mortem) con Windows 7 e versioni successive. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Misurare le prestazioni nelle build di rilascio

Gli strumenti nel profiler delle prestazioni hanno lo scopo di fornire analisi per le build di **rilascio** . Nel profiler delle prestazioni è possibile raccogliere informazioni di diagnostica durante l'esecuzione dell'app e quindi esaminare le informazioni raccolte dopo che l'app è stata arrestata (analisi post-mortem).

Aprire il profiler delle prestazioni scegliendo **debug**  >  **Performance Profiler** (o **ALT + F2**).

![Profiler prestazioni](../profiling/media/prof-tour-performance-profiler.png "Profiler prestazioni")

Per ulteriori informazioni sull'utilizzo dello strumento utilizzo CPU o utilizzo memoria nel profiler delle prestazioni e negli strumenti integrati nel debugger, vedere [eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Gli strumenti disponibili in Profiler prestazioni includono:

- [Utilizzo della CPU](../profiling/cpu-usage.md)
- [Allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md)
- [Utilizzo memoria](../profiling/memory-usage-without-debugging2.md)
- [Strumento asincrono .NET](../profiling/analyze-async.md)
- [Strumento database](../profiling/analyze-database.md)
- [Utilizzo GPU](../profiling/gpu-usage.md)

Per visualizzare il supporto dello strumento di profilatura per diversi tipi di app, vedere [quale strumento si deve usare?](#which-tool-should-i-use)

In alcuni scenari, la finestra consente di selezionare [più strumenti per la profilatura](../profiling/use-multiple-profiler-tools-simultaneously.md). Gli strumenti come Utilizzo CPU possono visualizzare dati complementari che agevolano l'analisi. È anche possibile usare il [Profiler della riga di comando](../profiling/profile-apps-from-command-line.md) per abilitare scenari che coinvolgono più strumenti di profilatura.

## <a name="examine-performance-using-perftips"></a>Esaminare le prestazioni con PerfTips

Spesso, il modo più semplice per visualizzare le informazioni sulle prestazioni consiste nell'usare [PerfTips](../profiling/perftips.md). Con PerfTips è possibile visualizzare le informazioni sulle prestazioni durante l'interazione con il codice. È possibile verificare informazioni quali la durata dell'evento, misurata da quando il debugger è stato messo pausa l'ultima volta o quando è stata avviata l'applicazione. Ad esempio, se si esegue il codice un'istruzione alla volta (F10, F11), PerfTips Mostra la durata di runtime dell'app dall'operazione del passaggio precedente al passaggio corrente.

![Panoramica della profilatura PerfTips](../profiling/media/prof-tour-perf-tips.png "Panoramica della profilatura PerfTips")

È possibile utilizzare PerfTips per esaminare il tempo necessario per l'esecuzione di un blocco di codice o il tempo necessario per il completamento di una singola funzione.

PerfTips Mostra gli stessi eventi che vengono visualizzati anche nella visualizzazione **eventi** del strumenti di diagnostica. Nella visualizzazione **eventi** è possibile visualizzare eventi diversi che si verificano durante il debug, ad esempio l'impostazione di un punto di interruzione o un'operazione di esecuzione del codice.

![Visualizzazione eventi Strumenti di diagnostica](../profiling/media/prof-tour-events.png "Strumenti di diagnostica visualizzare gli eventi")

 > [!NOTE]
 > Gli utenti di Visual Studio Enterprise possono visualizzare anche gli [eventi IntelliTrace](../debugger/intellitrace.md) in questa scheda.

## <a name="analyze-cpu-usage"></a>Analizzare l'utilizzo della CPU

L'uso dello strumento Utilizzo CPU è consigliabile per iniziare ad analizzare le prestazioni dell'applicazione. Lo strumento offre maggiori informazioni sulle risorse della CPU consumate dall'applicazione. È possibile utilizzare lo [strumento utilizzo CPU integrato del debugger](../profiling/beginners-guide-to-performance-profiling.md) o lo [strumento di utilizzo della CPU post-mortem](../profiling/cpu-usage.md).

Quando si usa lo strumento utilizzo CPU integrato del debugger, aprire la finestra degli strumenti di diagnostica, se è chiusa, scegliere **debug/Windows/mostra strumenti di diagnostica**. Durante il debug, aprire la visualizzazione  **Riepilogo** e selezionare **registra profilo CPU**.

![Abilitare l'utilizzo della CPU nell'Strumenti di diagnostica](../profiling/media/prof-tour-enable-cpu-profiling.png "Strumenti di diagnostica Abilita utilizzo CPU")

Un modo per usare lo strumento consiste nell'impostare due punti di interruzione nel codice, uno all'inizio e uno alla fine della funzione o l'area di codice da analizzare. Esaminare i dati di profilatura durante la pausa in corrispondenza del secondo punto di interruzione.

La visualizzazione **Utilizzo CPU** contiene un elenco di funzioni ordinate in base a quelle in esecuzione da tempo, con la funzione di maggior durata in cima all'elenco. In questo modo è possibile sapere quali sono le funzioni in cui si verificano colli di bottiglia delle prestazioni.

![Visualizzazione utilizzo CPU Strumenti di diagnostica](../profiling/media/prof-tour-cpu-usage.png "Utilizzo della CPU Strumenti di diagnostica")

Fare doppio clic su una funzione a cui si è interessati per aprire una visualizzazione più dettagliata a tre riquadri in modalità "farfalla", con la funzione selezionata al centro della finestra, la funzione chiamante a sinistra e le funzioni chiamate a destra. La sezione **Corpo funzione** indica la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. Questi dati consentono di valutare se la funzione stessa è un collo di bottiglia delle prestazioni.

![Visualizzazione "Butterfly" del chiamante Strumenti di diagnostica](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Visualizzazione chiamata del chiamante Strumenti di diagnostica")

## <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

La finestra **strumenti di diagnostica** consente inoltre di valutare l'utilizzo della memoria nell'app utilizzando lo strumento **utilizzo memoria** . Ad esempio, è possibile esaminare il numero e le dimensioni degli oggetti nell'heap. È possibile utilizzare lo [strumento utilizzo memoria integrato nel debugger](../profiling/memory-usage.md) o lo [strumento utilizzo memoria post-mortem](../profiling/memory-usage-without-debugging2.md) nel profiler delle prestazioni.

Gli sviluppatori .NET possono scegliere tra lo [strumento di allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md) o lo strumento [utilizzo memoria](../profiling/memory-usage.md) .

- Lo strumento di **allocazione oggetti .NET** consente di identificare i modelli di allocazione e le anomalie nel codice .NET e consente di identificare i problemi più comuni con Garbage Collection. Questo strumento viene eseguito solo come strumento post-mortem. È possibile eseguire questo strumento in computer locali o remoti.
- Lo strumento **utilizzo memoria** è utile per identificare le perdite di memoria, che in genere non sono comuni nelle app .NET. Se è necessario utilizzare le funzionalità del debugger durante il controllo della memoria, ad esempio l'esecuzione di un'istruzione alla volta nel codice, è consigliabile usare lo strumento [utilizzo memoria integrato del debugger](../profiling/beginners-guide-to-performance-profiling.md) .

Per analizzare l'utilizzo della memoria con lo strumento **utilizzo memoria** , è necessario eseguire almeno uno snapshot della memoria. Spesso, il modo migliore per analizzare la memoria consiste nel creare due snapshot: il primo immediatamente prima di un sospetto problema di memoria e il secondo subito dopo che si è verificato un sospetto problema di memoria. È quindi possibile confrontare i due snapshot in una visualizzazione differenziale e vedere esattamente che cosa è cambiato. Nella figura seguente viene illustrato l'acquisizione di uno snapshot con lo strumento integrato nel debugger.

![Creazione di uno snapshot nella Strumenti di diagnostica](../profiling/media/prof-tour-take-snapshots.gif "Strumenti di diagnostica creare snapshot")

Quando si seleziona uno dei collegamenti a freccia, viene fornita una visualizzazione differenziale dell'heap (un aumento di utilizzo della ![memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento utilizzo memoria") per le frecce rosse Mostra un numero crescente di oggetti (a sinistra) o una dimensione heap crescente (Right). Se si sceglie il collegamento a destra, si ottiene una visualizzazione differenziale dell'heap ordinata in base agli oggetti che hanno contribuito di più all'aumento delle dimensioni dell'heap. Ciò consente di individuare i problemi di memoria. Ad esempio, nell'illustrazione riportata di seguito, i byte usati dagli oggetti `ClassHandlersStore` sono aumentati di 3.492 byte nel secondo snapshot.

![Visualizzazione diff heap Strumenti di diagnostica](../profiling/media/prof-tour-mem-usage-diff-heap.png "Visualizzazione diff heap Strumenti di diagnostica")

Se invece si fa clic sul collegamento a sinistra nella visualizzazione **Utilizzo memoria**, la visualizzazione dell'heap è organizzata in base al numero di oggetti. Gli oggetti di un tipo particolare il cui numero è aumentato maggiormente appaiono in cima all'elenco (ordinati in base alla colonna **Diff. conteggio**).

## <a name="analyze-resource-consumption-xaml"></a>Analizzare l'uso di risorse (XAML)

Nelle app XAML, ad esempio le app WPF desktop di Windows e le app UWP, è possibile analizzare il consumo di risorse usando lo strumento Sequenza temporale applicazione. È possibile ad esempio analizzare il tempo impiegato dall'applicazione per preparare i frame dell'interfaccia utente (layout e rendering), per soddisfare le richieste di rete e disco e in scenari come l'avvio dell'applicazione, il caricamento delle pagine e il ridimensionamento di Windows. Per usare lo strumento, scegliere **Sequenza temporale dell'applicazione** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario con un sospetto problema di consumo delle risorse e quindi scegliere **Arresta raccolta** per generare il report.

I framerate ridotti nel grafico della **velocità effettiva degli elementi visivi** possono corrispondere a problemi di visualizzazione che si riscontrano quando si esegue l'applicazione. Analogamente, i numeri elevati nell'**utilizzo dei thread di interfaccia utente** possono corrispondere a problemi di velocità di risposta dell'interfaccia utente. Nel report è possibile selezionare un periodo di tempo con un sospetto problema di prestazioni e quindi esaminare in dettaglio le attività del thread dell'interfaccia utente nella visualizzazione Dettagli sequenza temporale (riquadro inferiore).

![Strumento di profilatura Sequenza temporale applicazione](../profiling/media/prof-tour-application-timeline.gif "Panoramica della profilatura Sequenza temporale applicazione")

Nella visualizzazione dei dettagli della sequenza temporale è possibile trovare informazioni come il tipo di attività (o l'elemento dell'interfaccia utente) insieme alla durata dell'attività. Ad esempio, nella figura un evento **Layout** per un controllo Grid impiega 57,53 ms.

Per altre informazioni, vedere [Sequenza temporale dell'applicazione](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Esaminare gli eventi dell'applicazione

Il [Visualizzatore eventi](../profiling/events-viewer.md) generici consente di visualizzare l'attività dell'applicazione tramite un elenco di eventi, ad esempio il caricamento del modulo, l'avvio del thread e le configurazioni di sistema, per facilitare la diagnosi del modo in cui l'applicazione viene eseguita direttamente nel profiler di Visual Studio. Questo strumento è disponibile nel profiler delle prestazioni. Aprire il profiler delle prestazioni scegliendo **debug**  >  **Performance Profiler** (o **ALT + F2**).

Lo strumento Mostra ogni evento in una visualizzazione elenco. Le colonne forniscono informazioni su ogni evento, ad esempio il nome dell'evento, il timestamp e l'ID del processo.

![Traccia Visualizzatore eventi](../profiling/media/eventviewertrace.png "Traccia Visualizzatore eventi")

## <a name="analyze-asynchronous-code-net"></a>Analizzare il codice asincrono (.NET)

Lo [strumento .NET Async](../profiling/analyze-async.md) consente di analizzare le prestazioni del codice asincrono nell'applicazione. Questo strumento è disponibile nel profiler delle prestazioni. Aprire il profiler delle prestazioni scegliendo **debug**  >  **Performance Profiler** (o **ALT + F2**).

Lo strumento Mostra ogni operazione asincrona in una visualizzazione elenco. È possibile visualizzare informazioni quali l'ora di inizio, l'ora di fine e il tempo totale per un'operazione asincrona.

![Lo strumento .NET Async è stato arrestato](../profiling/media/async-tool-opened.png "Lo strumento .NET Async è stato arrestato")

## <a name="analyze-database-performance-net-core"></a>Analizzare le prestazioni del database (.NET Core)

Per le app .NET Core che usano ADO.NET o Entity Framework Core, lo [strumento di database](../profiling/analyze-database.md) consente di registrare le query del database eseguite dall'applicazione durante una sessione di diagnostica. È quindi possibile analizzare le informazioni sulle singole query per individuare le posizioni in cui è possibile migliorare le prestazioni dell'app. Questo strumento è disponibile nel profiler delle prestazioni. Aprire il profiler delle prestazioni scegliendo **debug**  >  **Performance Profiler** (o **ALT + F2**).

Lo strumento Mostra ogni query in una visualizzazione elenco. È possibile visualizzare informazioni quali l'ora di inizio e la durata della query.

![Allocation (Allocazione)](./media/db-gotosource.png "Allocation (Allocazione)")

## <a name="visualize-net-counters-net-core"></a>Visualizzare i contatori .NET (.NET Core)

A partire da Visual Studio 2019 versione 16,7, è possibile usare lo [strumento contatori .NET](../profiling/dotnet-counters-tool.md) in Visual Studio per visualizzare i contatori delle prestazioni. È possibile visualizzare i contatori creati usando i [contatori DotNet](/dotnet/core/diagnostics/dotnet-counters). i contatori DotNet supportano molti contatori, ad esempio l'utilizzo della CPU e le dimensioni dell'heap Garbage Collector.

Lo strumento Mostra i valori Live per ogni contatore in una visualizzazione elenco.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Raccolta di strumenti per contatori .NET.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Esaminare le prestazioni dell'interfaccia utente e gli eventi di accessibilità (piattaforma UWP)

Nelle app UWP è possibile abilitare l' **analisi dell'interfaccia utente** nella finestra **strumenti di diagnostica** . Lo strumento cerca i comuni problemi di prestazioni o accessibilità e li indica nella visualizzazione **Eventi** durante il debug. Le descrizioni degli eventi contengono informazioni che possono essere utili per risolvere i problemi.

![Visualizzazione degli eventi di analisi dell'interfaccia utente negli strumenti di diagnostica](../profiling/media/prof-tour-ui-analysis.png "Strumenti di diagnostica visualizzare gli eventi di analisi dell'interfaccia utente")

## <a name="analyze-gpu-usage-direct3d"></a>Analizzare l'uso della GPU (Direct3D)

Nelle applicazioni Direct3D (i componenti Direct3D devono essere in C++) è possibile esaminare l'attività sulla GPU e analizzare i problemi di prestazioni. Per altre informazioni, vedere l'articolo relativo all'[uso della GPU](./gpu-usage.md). Per usare lo strumento, scegliere **Utilizzo GPU** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che interessa per la profilatura e quindi scegliere **Arresta raccolta** per generare un report.

Quando si seleziona un periodo di tempo nei grafici e si sceglie **Visualizza dettagli**, appare una visualizzazione dettagliata nel riquadro inferiore. Nella visualizzazione dettagliata è possibile esaminare l'entità dell'attività in corso in ogni CPU e GPU. Selezionare gli eventi nel riquadro inferiore per ottenere i popup nella sequenza temporale. Ad esempio, selezionare l'evento **Present** per visualizzare i popup delle chiamate **presenti**. (Le linee verticali VSync verticali chiare possono essere usate come riferimento per capire se alcune chiamate **presenti** non sono state perse vsync. Per consentire all'app di raggiungere 60 FPS, deve essere presente una chiamata **presente** tra ogni due VSyncs.

![Strumento di profilatura utilizzo GPU](../profiling/media/prof-tour-gpu-usage.png "Utilizzo GPU diag")

È anche possibile usare i grafici per determinare se esistono colli di bottiglia delle prestazioni associati alla CPU o GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analizzare le prestazioni (JavaScript UWP)

Per le app UWP è possibile usare lo strumento Memoria JavaScript e lo strumento Velocità di risposta interfaccia utente HTML.

Lo strumento Memoria JavaScript è simile allo strumento Utilizzo memoria disponibile per altri tipi di applicazioni. È possibile usare questo strumento per comprendere in che modo viene usata la memoria e individuare le perdite di memoria nell'applicazione. Per maggiori dettagli sullo strumento, vedere [Memoria JavaScript](../profiling/javascript-memory.md).

![Strumento di profilatura della memoria JavaScript](../profiling/media/diagjsmemory.png "Finestra")

Per diagnosticare la velocità di risposta dell'interfaccia utente, i tempi di caricamento lenti e gli aggiornamenti visivi lenti nelle app UWP, usare lo strumento Velocità di risposta interfaccia utente HTML. L'uso è simile a quello dello strumento Sequenza temporale dell'applicazione per altri tipi di applicazioni. Per altre informazioni, vedere [Velocità di risposta dell'interfaccia utente HTML](../profiling/html-ui-responsiveness.md).

![Strumento di profilatura della velocità di risposta interfaccia utente HTML](../profiling/media/diaghtmlresp.png "Finestra")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analizzare l'uso della rete (piattaforma UWP)

Nelle app UWP è possibile analizzare le operazioni di rete eseguite con l' `Windows.Web.Http` API. Questo strumento può essere utile per risolvere problemi quali problemi di accesso e autenticazione, uso errato della cache e prestazioni di visualizzazione e download scarse. Per usare lo strumento, scegliere **Rete** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura utilizzo rete](../profiling/media/prof-tour-network-usage.png "Utilizzo rete diag")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "Dettagli sull'utilizzo della rete diag")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizzare le prestazioni (strumenti legacy)

::: moniker range="vs-2017"
Se sono necessarie funzionalità, ad esempio la strumentazione, che non sono attualmente presenti negli strumenti Utilizzo CPU o Utilizzo memoria e si eseguono applicazioni desktop o ASP.NET, è possibile usare Esplora prestazioni per la profilatura. Lo strumento non è supportato nelle app UWP. Per altre informazioni, vedere [Esplora prestazioni](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
In Visual Studio 2019, il Esplora prestazioni legacy e gli strumenti di profilatura correlati, ad esempio la creazione guidata sessione di prestazioni, sono stati ridotti nel profiler delle prestazioni, che è possibile aprire utilizzando **debug**  >  **Performance Profiler**. Nel profiler delle prestazioni, gli strumenti di diagnostica disponibili dipendono dalla destinazione scelta e dal progetto di avvio aperto corrente. Lo strumento utilizzo CPU fornisce la funzionalità di campionamento precedentemente supportata nella creazione guidata sessione di prestazioni. Lo strumento di strumentazione fornisce la funzionalità di profilatura instrumentata (per i conteggi e le durate esatte) che era nella creazione guidata sessione di prestazioni. Nel profiler delle prestazioni vengono visualizzati anche altri strumenti di memoria.
::: moniker-end

![Strumento Esplora prestazioni](../profiling/media/prof-tour-performance-explorer.png "Esplora prestazioni")

## <a name="which-tool-should-i-use"></a>Quale strumento si deve usare?

Nella tabella seguente sono riportati i diversi strumenti offerti da Visual Studio e i diversi tipi di progetto con cui possono essere usati:

::: moniker range=">=vs-2019"
|Strumento di prestazioni|Desktop di Windows|Piattaforma UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[PerfTips](../profiling/perftips.md)|sì|sì|sì|
|[Utilizzo CPU](../profiling/beginners-guide-to-performance-profiling.md)|sì|sì|sì|
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|
|[Allocazione oggetti .NET](../profiling/dotnet-alloc-tool.md)|Sì (solo .NET)|sì|sì|
|[Utilizzo GPU](./gpu-usage.md)|sì|sì|no|
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|Sì (XAML)|sì|no|
|[Visualizzatore eventi](../profiling/events-viewer.md)|sì|sì|sì|
|[.NET Async](../profiling/analyze-async.md)|Sì (solo .NET)|sì|sì|
|[Contatori .NET](../profiling/dotnet-counters-tool.md)|Sì (solo .NET Core)|no|Sì (solo ASP.NET Core)|
|[Database](../profiling/analyze-database.md)|Sì (solo .NET Core)|no|Sì (solo ASP.NET Core)|
|[Esplora prestazioni](#analyze-performance-legacy-tools)|no|no|no|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Strumento di prestazioni|Desktop di Windows|Piattaforma UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Utilizzo CPU](../profiling/beginners-guide-to-performance-profiling.md)|sì|sì|sì|
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|
|[Utilizzo GPU](./gpu-usage.md)|sì|sì|no|
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|Sì (XAML)|sì|no|
|[PerfTips](../profiling/perftips.md)|sì|Sì per XAML, no per HTML|sì|
|[Esplora prestazioni](../profiling/performance-explorer.md)|sì|no|sì|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
|[Utilizzo rete](../profiling/network-usage.md)|no|sì|no|
|[Velocità di risposta interfaccia utente HTML](../profiling/html-ui-responsiveness.md)|no|Sì per HTML, no per XAML|no|
|[Memoria JavaScript](../profiling/javascript-memory.md)|no|Sì per HTML, no per XAML|no|
::: moniker-end


## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/debugger-feature-tour.md)