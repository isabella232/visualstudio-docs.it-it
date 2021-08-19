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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c0b3bb8102020e7b091ea7c6127f449b4ef70eca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038695"
---
# <a name="first-look-at-profiling-tools"></a>Presentazione degli strumenti di profilatura

Visual Studio offre un'ampia gamma di strumenti di profilatura che consentono di diagnosticare diversi tipi di problemi di prestazioni in base al tipo di app. Questo articolo illustra rapidamente gli strumenti di profilatura più comuni.

Per visualizzare il supporto dello strumento di profilatura per diversi tipi di app, vedere [Quale strumento è consigliabile usare?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Misurare le prestazioni durante il debug

Gli strumenti di profilatura a cui è possibile accedere durante una sessione di debug sono disponibili nella finestra Strumenti di diagnostica. La finestra Strumenti di diagnostica viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare la finestra, fare clic su **Debug/Windows/Mostra** Strumenti di diagnostica (o premere   +  **CTRL ALT**  +  **F2).** Con finestra aperta è possibile selezionare gli strumenti per cui si vogliono raccogliere dati.

![Strumenti di diagnostica finestra](../profiling/media/prof-tour-diagnostic-tools.png "Strumenti di diagnostica")

Durante il debug è possibile usare la finestra **Strumenti di diagnostica** per l'analisi della CPU e dell'uso della memoria e si possono visualizzare gli eventi che generano informazioni relative alle prestazioni.

![Strumenti di diagnostica visualizzazione Riepilogo](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Strumenti di diagnostica riepilogo")

La **Strumenti di diagnostica** è un modo comune per profilare le app, ma per le build di versione è anche possibile eseguire un'analisi post-mortem dell'app. Per altre informazioni sui diversi approcci, vedere [Eseguire strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Per visualizzare il supporto dello strumento di profilatura per diversi tipi di app, vedere [Quale strumento è consigliabile usare?](#which-tool-should-i-use)

Gli strumenti disponibili nella finestra Strumenti di diagnostica o durante una sessione di debug includono:
- [Utilizzo CPU](../profiling/beginners-guide-to-performance-profiling.md)
- [Utilizzo memoria](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**. È possibile usare gli [strumenti post-mortem](#post_mortem) con Windows 7 e versioni successive. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Misurare le prestazioni nelle build di versione

Gli strumenti nel Profiler prestazioni sono destinati a fornire l'analisi per le build **di** versione. Nel Profiler prestazioni è possibile raccogliere informazioni di diagnostica mentre l'app è in esecuzione e quindi esaminare le informazioni raccolte dopo l'arresto dell'app (un'analisi post-mortem).

Aprire il Profiler prestazioni **scegliendo** Debug  >  **Profiler prestazioni** (o **ALT+F2).**

![Profiler prestazioni](../profiling/media/prof-tour-performance-profiler.png "Profiler prestazioni")

Per altre informazioni sull'uso dello strumento Utilizzo CPU o Utilizzo memoria nel Profiler prestazioni rispetto agli strumenti integrati nel debugger, vedere Eseguire gli strumenti di profilatura con o [senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Gli strumenti disponibili nella Profiler prestazioni includono:

- [Utilizzo CPU](../profiling/cpu-usage.md)
- [Allocazione di oggetti .NET](../profiling/dotnet-alloc-tool.md)
- [Utilizzo memoria](../profiling/memory-usage-without-debugging2.md)
- [Strumento asincrono .NET](../profiling/analyze-async.md)
- [Strumento database](../profiling/analyze-database.md)
- [Utilizzo della GPU](../profiling/gpu-usage.md)

Per visualizzare il supporto dello strumento di profilatura per diversi tipi di app, vedere [Quale strumento è consigliabile usare?](#which-tool-should-i-use)

In alcuni scenari, la finestra consente di selezionare [più strumenti di profilatura](../profiling/use-multiple-profiler-tools-simultaneously.md). Gli strumenti come Utilizzo CPU possono visualizzare dati complementari che agevolano l'analisi. È anche possibile usare il [profiler della riga di comando per](../profiling/profile-apps-from-command-line.md) abilitare scenari che coinvolgono più strumenti di profilatura.

## <a name="examine-performance-using-perftips"></a>Esaminare le prestazioni usando i suggerimenti perftip

Spesso, il modo più semplice per visualizzare le informazioni sulle prestazioni è usare [PerfTips](../profiling/perftips.md). Usando PerfTips è possibile visualizzare le informazioni sulle prestazioni durante l'interazione con il codice. È possibile verificare informazioni quali la durata dell'evento, misurata da quando il debugger è stato messo pausa l'ultima volta o quando è stata avviata l'applicazione. Ad esempio, se si esegue un'istruzione alla volta il codice (F10, F11), PerfTips mostra la durata del runtime dell'app dall'operazione del passaggio precedente al passaggio corrente.

![Suggerimenti per la presentazione della profilatura](../profiling/media/prof-tour-perf-tips.png "PerfTips della presentazione della profilatura")

È possibile usare PerfTips per esaminare il tempo necessario per l'esecuzione di un blocco di codice o il tempo necessario per il completamento di una singola funzione.

PerfTips mostra gli stessi eventi visualizzati anche nella **visualizzazione** Eventi del Strumenti di diagnostica. Nella visualizzazione **Eventi** è possibile visualizzare diversi eventi che si verificano durante il debug, ad esempio l'impostazione di un punto di interruzione o un'operazione di esecuzione di istruzioni del codice.

![Strumenti di diagnostica eventi](../profiling/media/prof-tour-events.png "Strumenti di diagnostica eventi di visualizzazione")

 > [!NOTE]
 > Gli utenti di Visual Studio Enterprise possono visualizzare anche gli [eventi IntelliTrace](../debugger/intellitrace.md) in questa scheda.

## <a name="analyze-cpu-usage"></a>Analizzare l'utilizzo della CPU

L'uso dello strumento Utilizzo CPU è consigliabile per iniziare ad analizzare le prestazioni dell'applicazione. Lo strumento offre maggiori informazioni sulle risorse della CPU consumate dall'applicazione. È possibile usare lo strumento [Utilizzo CPU integrato](../profiling/beginners-guide-to-performance-profiling.md) nel debugger o lo strumento Utilizzo CPU [post-mortem](../profiling/cpu-usage.md).

Quando si usa lo strumento Utilizzo CPU integrato nel debugger, aprire la finestra Strumento di diagnostica (se è chiusa, scegliere **Debug/Windows/Mostra** Strumenti di diagnostica ). Durante il debug, aprire  **la visualizzazione Riepilogo** e selezionare Registra profilo **CPU**.

![Abilitare l'utilizzo della CPU nel Strumenti di diagnostica](../profiling/media/prof-tour-enable-cpu-profiling.png "Strumenti di diagnostica l'utilizzo della CPU")

Un modo per usare lo strumento è impostare due punti di interruzione nel codice, uno all'inizio e uno alla fine della funzione o l'area di codice da analizzare. Esaminare i dati di profilatura durante la pausa in corrispondenza del secondo punto di interruzione.

La visualizzazione **Utilizzo CPU** contiene un elenco di funzioni ordinate in base a quelle in esecuzione da tempo, con la funzione di maggior durata in cima all'elenco. In questo modo è possibile sapere quali sono le funzioni in cui si verificano colli di bottiglia delle prestazioni.

![Strumenti di diagnostica utilizzo CPU](../profiling/media/prof-tour-cpu-usage.png "Strumenti di diagnostica utilizzo della CPU")

Fare doppio clic su una funzione a cui si è interessati per aprire una visualizzazione più dettagliata a tre riquadri in modalità "farfalla", con la funzione selezionata al centro della finestra, la funzione chiamante a sinistra e le funzioni chiamate a destra. La sezione **Corpo funzione** indica la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. Questi dati consentono di valutare se la funzione stessa è un collo di bottiglia delle prestazioni.

![Strumenti di diagnostica visualizzazione "a forma di fiori" del chiamante chiamato](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Strumenti di diagnostica chiamante chiamato")

## <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

La **Strumenti di diagnostica** consente anche di valutare l'utilizzo della memoria nell'app usando lo **strumento Utilizzo memoria.** Ad esempio, è possibile esaminare il numero e le dimensioni degli oggetti nell'heap. È possibile usare lo [strumento Utilizzo memoria integrato](../profiling/memory-usage.md) nel debugger o lo strumento Utilizzo memoria [post-mortem](../profiling/memory-usage-without-debugging2.md) nel Profiler prestazioni.

Gli sviluppatori .NET possono scegliere tra lo strumento di allocazione [di oggetti .NET](../profiling/dotnet-alloc-tool.md) o lo [strumento Utilizzo memoria.](../profiling/memory-usage.md)

- Lo **strumento di allocazione** di oggetti .NET consente di identificare i modelli di allocazione e le anomalie nel codice .NET e consente di identificare i problemi comuni relativi a Garbage Collection. Questo strumento viene eseguito solo come strumento post-mortem. È possibile eseguire questo strumento in computer locali o remoti.
- Lo **strumento Utilizzo memoria** è utile per identificare le perdite di memoria, che in genere non sono comuni nelle app .NET. Se è necessario usare le funzionalità del debugger durante il controllo della memoria, ad esempio l'esecuzione di codice un'istruzione alla volta, è consigliabile usare lo strumento di utilizzo della memoria integrato [nel debugger.](../profiling/beginners-guide-to-performance-profiling.md)

Per analizzare l'utilizzo della memoria con lo strumento **Utilizzo** memoria, è necessario creare almeno uno snapshot della memoria. Spesso, il modo migliore per analizzare la memoria consiste nel creare due snapshot: il primo immediatamente prima di un sospetto problema di memoria e il secondo subito dopo che si è verificato un sospetto problema di memoria. È quindi possibile confrontare i due snapshot in una visualizzazione differenziale e vedere esattamente che cosa è cambiato. Nella figura seguente viene illustrato come creare uno snapshot con lo strumento integrato nel debugger.

![Creare uno snapshot nel Strumenti di diagnostica](../profiling/media/prof-tour-take-snapshots.gif "Strumenti di diagnostica creare snapshot")

Quando si seleziona uno dei collegamenti a freccia, viene visualizzata una visualizzazione differenziale dell'heap (una freccia rivolta verso l'alto rossa ![Aumento](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento dell'utilizzo della memoria") utilizzo memoria mostra un numero crescente di oggetti (a sinistra) o una dimensione dell'heap crescente (a destra)). Se si sceglie il collegamento a destra, si ottiene una visualizzazione differenziale dell'heap ordinata in base agli oggetti che hanno contribuito di più all'aumento delle dimensioni dell'heap. Ciò consente di individuare i problemi di memoria. Ad esempio, nell'illustrazione riportata di seguito, i byte usati dagli oggetti `ClassHandlersStore` sono aumentati di 3.492 byte nel secondo snapshot.

![Strumenti di diagnostica diff heap](../profiling/media/prof-tour-mem-usage-diff-heap.png "Strumenti di diagnostica delle diff heap")

Se invece si fa clic sul collegamento a sinistra nella visualizzazione **Utilizzo memoria**, la visualizzazione dell'heap è organizzata in base al numero di oggetti. Gli oggetti di un tipo particolare il cui numero è aumentato maggiormente appaiono in cima all'elenco (ordinati in base alla colonna **Diff. conteggio**).

## <a name="analyze-resource-consumption-xaml"></a>Analizzare l'uso di risorse (XAML)

Nelle app XAML, ad esempio le app WPF desktop di Windows e le app UWP, è possibile analizzare il consumo di risorse usando lo strumento Sequenza temporale applicazione. È possibile ad esempio analizzare il tempo impiegato dall'applicazione per preparare i frame dell'interfaccia utente (layout e rendering), per soddisfare le richieste di rete e disco e in scenari come l'avvio dell'applicazione, il caricamento delle pagine e il ridimensionamento di Windows. Per usare lo strumento, scegliere **Sequenza temporale dell'applicazione** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario con un sospetto problema di consumo delle risorse e quindi scegliere **Arresta raccolta** per generare il report.

I framerate ridotti nel grafico della **velocità effettiva degli elementi visivi** possono corrispondere a problemi di visualizzazione che si riscontrano quando si esegue l'applicazione. Analogamente, i numeri elevati nell'**utilizzo dei thread di interfaccia utente** possono corrispondere a problemi di velocità di risposta dell'interfaccia utente. Nel report è possibile selezionare un periodo di tempo con un sospetto problema di prestazioni e quindi esaminare in dettaglio le attività del thread dell'interfaccia utente nella visualizzazione Dettagli sequenza temporale (riquadro inferiore).

![Sequenza temporale applicazione di profilatura](../profiling/media/prof-tour-application-timeline.gif "Presentazione della profilatura Sequenza temporale applicazione")

Nella visualizzazione Dettagli sequenza temporale è possibile trovare informazioni quali il tipo di attività (o l'elemento dell'interfaccia utente interessato) insieme alla durata dell'attività. Ad esempio, nella figura un evento **Layout** per un controllo Grid impiega 57,53 ms.

Per altre informazioni, vedere [Sequenza temporale dell'applicazione](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Esaminare gli eventi dell'applicazione

Il [](../profiling/events-viewer.md) visualizzatore di eventi generici consente di visualizzare l'attività dell'applicazione tramite un elenco di eventi, ad esempio il caricamento del modulo, l'avvio di thread e le configurazioni di sistema, per diagnosticare meglio le prestazioni dell'applicazione all'interno del profiler Visual Studio. Questo strumento è disponibile nel Profiler prestazioni. Aprire il Profiler prestazioni scegliendo **Debug**  >  **Profiler prestazioni** (o **ALT+F2).**

Lo strumento mostra ogni evento in una visualizzazione elenco. Le colonne forniscono informazioni su ogni evento, ad esempio il nome dell'evento, il timestamp e l'ID processo.

![Visualizzatore eventi traccia](../profiling/media/eventviewertrace.png "Visualizzatore eventi traccia")

## <a name="analyze-asynchronous-code-net"></a>Analizzare il codice asincrono (.NET)

Lo [.NET Async consente](../profiling/analyze-async.md) di analizzare le prestazioni del codice asincrono nell'applicazione. Questo strumento è disponibile nel Profiler prestazioni. Aprire il Profiler prestazioni scegliendo **Debug**  >  **Profiler prestazioni** (o **ALT+F2).**

Lo strumento mostra ogni operazione asincrona in una visualizzazione elenco. È possibile visualizzare informazioni quali l'ora di inizio, l'ora di fine e l'ora totale per un'operazione asincrona.

![.NET Async Strumento arrestato](../profiling/media/async-tool-opened.png ".NET Async Strumento arrestato")

## <a name="analyze-database-performance-net-core"></a>Analizzare le prestazioni del database (.NET Core)

Per le app .NET Core che usano ADO.NET o Entity Framework Core, lo strumento [Database](../profiling/analyze-database.md) consente di registrare le query di database eseguite dall'applicazione durante una sessione di diagnostica. È quindi possibile analizzare le informazioni sulle singole query per trovare le posizioni in cui è possibile migliorare le prestazioni dell'app. Questo strumento è disponibile nel Profiler prestazioni. Aprire il Profiler prestazioni scegliendo **Debug**  >  **Profiler prestazioni** (o **ALT+F2).**

Lo strumento mostra ogni query in una visualizzazione elenco. È possibile visualizzare informazioni quali l'ora di inizio e la durata della query.

![Allocation (Allocazione)](./media/db-gotosource.png "Allocation (Allocazione)")

## <a name="visualize-net-counters-net-core"></a>Visualizzare i contatori .NET (.NET Core)

A partire Visual Studio 2019 versione 16.7, è possibile usare lo strumento Contatori [.NET](../profiling/dotnet-counters-tool.md) in Visual Studio per visualizzare i contatori delle prestazioni. È possibile visualizzare i contatori creati usando [i contatori dotnet](/dotnet/core/diagnostics/dotnet-counters). I contatori dotnet supportano molti contatori, ad esempio l'utilizzo della CPU e le dimensioni dell'heap del Garbage Collector.

Lo strumento mostra i valori in tempo reale per ogni contatore in una visualizzazione elenco.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Raccolta dello strumento contatore .NET.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Esaminare le prestazioni dell'interfaccia utente e gli eventi di accessibilità (piattaforma UWP)

Nelle app UWP è possibile abilitare **l'analisi dell'interfaccia** utente **nella Strumenti di diagnostica** finestra. Lo strumento cerca i comuni problemi di prestazioni o accessibilità e li indica nella visualizzazione **Eventi** durante il debug. Le descrizioni degli eventi contengono informazioni che possono essere utili per risolvere i problemi.

![Visualizzare gli eventi di analisi dell'interfaccia utente negli strumenti di diagnostica](../profiling/media/prof-tour-ui-analysis.png "Strumenti di diagnostica visualizzare gli eventi di analisi dell'interfaccia utente")

## <a name="analyze-gpu-usage-direct3d"></a>Analizzare l'uso della GPU (Direct3D)

Nelle applicazioni Direct3D (i componenti Direct3D devono essere in C++) è possibile esaminare l'attività sulla GPU e analizzare i problemi di prestazioni. Per altre informazioni, vedere l'articolo relativo all'[uso della GPU](./gpu-usage.md). Per usare lo strumento, scegliere **Utilizzo GPU** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che interessa per la profilatura e quindi scegliere **Arresta raccolta** per generare un report.

Quando si seleziona un periodo di tempo nei grafici e si sceglie **Visualizza dettagli**, appare una visualizzazione dettagliata nel riquadro inferiore. Nella visualizzazione dettagliata è possibile esaminare l'entità dell'attività in corso in ogni CPU e GPU. Selezionare gli eventi nel riquadro inferiore per ottenere i popup nella sequenza temporale. Ad esempio, selezionare l'evento **Present** per visualizzare i popup delle chiamate **presenti**. Le linee VSync verticali di colore grigio chiaro possono essere usate come riferimento per determinare se alcune chiamate **presenti** hanno perso VSync. Deve essere presente una **chiamata Present** tra due VSync per consentire all'app di ottenere costantemente 60 FPS.

![Strumento di profilatura Utilizzo GPU](../profiling/media/prof-tour-gpu-usage.png "Diag GPU Usage")

È anche possibile usare i grafici per determinare se esistono colli di bottiglia delle prestazioni associati alla CPU o GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analizzare le prestazioni (JavaScript UWP)

Per le app UWP è possibile usare lo strumento Memoria JavaScript e lo strumento Velocità di risposta interfaccia utente HTML.

Lo strumento Memoria JavaScript è simile allo strumento Utilizzo memoria disponibile per altri tipi di applicazioni. È possibile usare questo strumento per comprendere in che modo viene usata la memoria e individuare le perdite di memoria nell'applicazione. Per maggiori dettagli sullo strumento, vedere [Memoria JavaScript](../profiling/javascript-memory.md).

![Strumento di profilatura della memoria JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Per diagnosticare la velocità di risposta dell'interfaccia utente, i tempi di caricamento lenti e gli aggiornamenti visivi lenti nelle app UWP, usare lo strumento Velocità di risposta interfaccia utente HTML. L'uso è simile a quello dello strumento Sequenza temporale dell'applicazione per altri tipi di applicazioni. Per altre informazioni, vedere [Velocità di risposta dell'interfaccia utente HTML](../profiling/html-ui-responsiveness.md).

![Strumento di profilatura velocità di risposta interfaccia utente HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analizzare l'uso della rete (piattaforma UWP)

Nelle app UWP è possibile analizzare le operazioni di rete eseguite usando `Windows.Web.Http` l'API. Questo strumento può essere utile per risolvere problemi come problemi di accesso e autenticazione, uso non corretto della cache e prestazioni di visualizzazione e download scarse. Per usare lo strumento, scegliere **Rete** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura Utilizzo rete](../profiling/media/prof-tour-network-usage.png "Diag Network Usage")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento Utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "Diag Network Usage Details")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizzare le prestazioni (strumenti legacy)

::: moniker range="vs-2017"
Se sono necessarie funzionalità, ad esempio la strumentazione, che non sono attualmente presenti negli strumenti Utilizzo CPU o Utilizzo memoria e si eseguono applicazioni desktop o ASP.NET, è possibile usare Esplora prestazioni per la profilatura. Lo strumento non è supportato nelle app UWP. Per altre informazioni, vedere [Esplora prestazioni](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
In Visual Studio 2019, l'Esplora prestazioni legacy e gli strumenti di profilatura correlati, ad esempio la Creazione guidata sessione di prestazioni, sono stati trasformati nel Profiler prestazioni, che è possibile aprire usando debug  >  **Profiler prestazioni**. Nel Profiler prestazioni, gli strumenti di diagnostica disponibili dipendono dalla destinazione scelta e dal progetto di avvio aperto corrente. Lo strumento Utilizzo CPU fornisce la funzionalità di campionamento supportata in precedenza nella Creazione guidata prestazioni. Lo strumento Strumentazione fornisce la funzionalità di profilatura instrumentata (per conteggi e durate precise delle chiamate) presente nella Creazione guidata sessione di prestazioni. Gli strumenti aggiuntivi per la memoria vengono visualizzati anche nel Profiler prestazioni.
::: moniker-end

![strumento Esplora prestazioni](../profiling/media/prof-tour-performance-explorer.png "Esplora prestazioni")

## <a name="which-tool-should-i-use"></a>Quale strumento si deve usare?

Nella tabella seguente sono riportati i diversi strumenti offerti da Visual Studio e i diversi tipi di progetto con cui possono essere usati:

::: moniker range=">=vs-2019"
|Strumento di prestazioni|Desktop di Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[PerfTips](../profiling/perftips.md)|sì|sì|sì|
|[Utilizzo CPU](../profiling/beginners-guide-to-performance-profiling.md)|sì|sì|sì|
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|
|[Allocazione di oggetti .NET](../profiling/dotnet-alloc-tool.md)|sì (solo .NET)|sì|sì|
|[Utilizzo GPU](./gpu-usage.md)|sì|sì|no|
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|yes (XAML)|sì|no|
|[Visualizzatore eventi](../profiling/events-viewer.md)|sì|sì|sì|
|[.NET Async](../profiling/analyze-async.md)|sì (solo .NET)|sì|sì|
|[Contatori .NET](../profiling/dotnet-counters-tool.md)|sì (solo .NET Core)|no|sì (solo ASP.NET Core)|
|[Database](../profiling/analyze-database.md)|sì (solo .NET Core)|no|sì (solo ASP.NET Core)|
|[Esplora prestazioni](#analyze-performance-legacy-tools)|no|no|no|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Strumento di prestazioni|Desktop di Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Utilizzo CPU](../profiling/beginners-guide-to-performance-profiling.md)|sì|sì|sì|
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|
|[Utilizzo GPU](./gpu-usage.md)|sì|sì|no|
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|yes (XAML)|sì|no|
|[PerfTips](../profiling/perftips.md)|sì|Sì per XAML, no per HTML|sì|
|[Esplora prestazioni](../profiling/performance-explorer.md)|sì|no|sì|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
|[Utilizzo della rete](../profiling/network-usage.md)|no|sì|no|
|[Velocità di risposta dell'interfaccia utente HTML](../profiling/html-ui-responsiveness.md)|no|Sì per HTML, no per XAML|no|
|[Memoria JavaScript](../profiling/javascript-memory.md)|no|Sì per HTML, no per XAML|no|
::: moniker-end


## <a name="see-also"></a>Vedi anche
- [Debug in Visual Studio](../debugger/debugger-feature-tour.md)