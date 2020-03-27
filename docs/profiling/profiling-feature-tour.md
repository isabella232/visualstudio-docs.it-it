---
title: Misurare le prestazioni con gli strumenti di profilatura
description: Esaminare una breve panoramica dei diversi strumenti di diagnostica disponibili in Visual Studio.
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2d23620a1861396971c79551088b898c9b77c86
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233102"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Avvio rapido: Presentazione degli strumenti di profilatura

Visual Studio offre un'ampia gamma di strumenti di profilatura che consentono di diagnosticare diversi tipi di problemi di prestazioni in base al tipo di app.

Gli strumenti di profilatura a cui è possibile accedere durante una sessione di debug sono disponibili nella finestra Strumenti di diagnostica. La finestra Strumenti di diagnostica viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare la finestra, fare clic su **Debug/Windows/Mostra strumenti di diagnostica**. Con finestra aperta è possibile selezionare gli strumenti per cui si vogliono raccogliere dati.

![Finestra Strumenti di diagnostica](../profiling/media/prof-tour-diagnostic-tools.png "Strumenti di diagnostica")

Durante il debug è possibile usare la finestra **Strumenti di diagnostica** per l'analisi della CPU e dell'uso della memoria e si possono visualizzare gli eventi che generano informazioni relative alle prestazioni.

![Visualizzazione Riepilogo strumenti di diagnostica](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Riepilogo degli strumenti di diagnostica")

La finestra **Strumenti di diagnostica** è spesso il modo migliore per profilare le app, ma per le build di versione è anche possibile effettuare un'analisi dopo che l'app è terminata. Per altre informazioni sui diversi approcci, vedere [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Per informazioni sugli strumenti di profilatura supportati per i diversi tipi di app, vedere [Quale strumento si deve usare?](#which-tool-should-i-use).

> [!NOTE]
> È possibile usare gli strumenti di valutazione finale con Windows 7 e versioni successive. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

## <a name="analyze-cpu-usage"></a>Analizzare l'utilizzo della CPU

L'uso dello strumento Utilizzo CPU è consigliabile per iniziare ad analizzare le prestazioni dell'applicazione. Lo strumento offre maggiori informazioni sulle risorse della CPU consumate dall'applicazione. Per una procedura dettagliata più dettagliata dello strumento Utilizzo CPU, vedere [Misurare le prestazioni dell'applicazione analizzando l'utilizzo della CPU](../profiling/beginners-guide-to-performance-profiling.md).

Dalla visualizzazione **Riepilogo** di Strumenti di diagnostica scegliere **Abilita profilatura CPU** (è necessario essere in una sessione di debug).

![Abilitare l'utilizzo della CPU negli strumenti di diagnosticaEnable CPU usage in the Diagnostic Tools](../profiling/media/prof-tour-enable-cpu-profiling.png "Strumenti di diagnostica Abilitare l'utilizzo della CPU")

Per usare lo strumento in modo più efficace, impostare due punti di interruzione nel codice, uno all'inizio e alla fine della funzione o dell'area di codice che si vuole analizzare. Esaminare i dati di profilatura durante la pausa in corrispondenza del secondo punto di interruzione.

La visualizzazione **Utilizzo CPU** contiene un elenco di funzioni ordinate in base a quelle in esecuzione da tempo, con la funzione di maggior durata in cima all'elenco. In questo modo è possibile sapere quali sono le funzioni in cui si verificano colli di bottiglia delle prestazioni.

![Visualizzazione Utilizzo CPU degli strumenti di diagnostica](../profiling/media/prof-tour-cpu-usage.png "Utilizzo CPU degli strumenti di diagnostica")

Fare doppio clic su una funzione a cui si è interessati per aprire una visualizzazione più dettagliata a tre riquadri in modalità "farfalla", con la funzione selezionata al centro della finestra, la funzione chiamante a sinistra e le funzioni chiamate a destra. La sezione **Corpo funzione** indica la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. Questi dati consentono di valutare se la funzione stessa è un collo di bottiglia delle prestazioni.

![Visualizzazione "farfalla" del chiamante degli strumenti di diagnostica](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Visualizzazione chiamate chiamante degli strumenti di diagnostica")

> [!TIP]
> Per analizzare le prestazioni, è anche possibile usare [PerfTips](#examine-performance-events-using-perftips) per eseguire il codice un'istruzione alla volta e identificare il tempo necessario per il completamento di determinate funzioni o blocchi di codice.

## <a name="examine-performance-events-using-perftips"></a>Esaminare gli eventi di prestazioni utilizzando PerfTipsExamine performance events using PerfTips

Spesso, il modo più semplice per visualizzare le informazioni sulle prestazioni consiste [nell'utilizzare PerfTips](../profiling/perftips.md). Utilizzando PerfTips, è possibile visualizzare le informazioni sulle prestazioni durante l'interazione con il codice. È possibile verificare informazioni quali la durata dell'evento, misurata da quando il debugger è stato messo pausa l'ultima volta o quando è stata avviata l'applicazione. Ad esempio, se esegui il codice (F10, F11), PerfTips mostra la durata del runtime dell'app dall'operazione del passaggio precedente al passaggio corrente.

![Profiling Tour PerfTips](../profiling/media/prof-tour-perf-tips.png "Profiling Tour PerfTips")

È possibile usare PerfTips per esaminare il tempo necessario per l'esecuzione di un blocco di codice o il tempo necessario per il completamento di una singola funzione.

PerfTips Mostra gli stessi eventi che vengono visualizzati anche nella visualizzazione **eventi** degli strumenti di diagnostica. Nella visualizzazione **Eventi** è possibile visualizzare diversi eventi che si verificano durante il debug, ad esempio l'impostazione di un punto di interruzione o un'operazione di esecuzione passoa del codice.

![Visualizzazione Eventi degli strumenti di diagnostica](../profiling/media/prof-tour-events.png "Eventi di visualizzazione degli strumenti di diagnostica")

 > [!NOTE]
 > Gli utenti di Visual Studio Enterprise possono visualizzare anche gli [eventi IntelliTrace](../debugger/intellitrace.md) in questa scheda.

## <a name="analyze-memory-usage"></a>Analizzare l'utilizzo della memoria

La finestra Strumenti di **diagnostica** consente inoltre di valutare l'utilizzo della memoria nell'app usando lo strumento **Utilizzo memoria.** Ad esempio, è possibile esaminare il numero e le dimensioni degli oggetti nell'heap. Per istruzioni più dettagliate sull'analisi della memoria, vedere [Analizzare l'utilizzo della memoria](../profiling/memory-usage.md). Un altro strumento di analisi della memoria, lo [strumento .NET Object Allocation](../profiling/dotnet-alloc-tool.md), consente di identificare i modelli di allocazione e le anomalie nel codice .NET.

Per analizzare l'utilizzo della memoria con l'utilizzo della memoria integrato nel debugger, è necessario creare almeno uno snapshot della memoria. Spesso, il modo migliore per analizzare la memoria consiste nel creare due snapshot: il primo immediatamente prima di un sospetto problema di memoria e il secondo subito dopo che si è verificato un sospetto problema di memoria. È quindi possibile confrontare i due snapshot in una visualizzazione differenziale e vedere esattamente che cosa è cambiato.

![Creare uno snapshot negli strumenti di diagnostica](../profiling/media/prof-tour-take-snapshots.gif "Strumenti di diagnostica Scattare istantanee")

Quando si seleziona uno dei collegamenti freccia, viene assegnata una visualizzazione differenziale dell'heap (una freccia rossa verso l'alto ![Aumento utilizzo memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento dell'utilizzo della memoria") mostra un numero di oggetti crescente (a sinistra) o una dimensione dell'heap crescente (a destra)). Se si sceglie il collegamento a destra, si ottiene una visualizzazione differenziale dell'heap ordinata in base agli oggetti che hanno contribuito di più all'aumento delle dimensioni dell'heap. Ciò consente di individuare i problemi di memoria. Ad esempio, nell'illustrazione riportata di seguito, i byte usati dagli oggetti `ClassHandlersStore` sono aumentati di 3.492 byte nel secondo snapshot.

![Visualizzazione diff heap degli strumenti di diagnostica](../profiling/media/prof-tour-mem-usage-diff-heap.png "Visualizzazione Diff heap degli strumenti di diagnostica")

Se invece si fa clic sul collegamento a sinistra nella visualizzazione **Utilizzo memoria**, la visualizzazione dell'heap è organizzata in base al numero di oggetti. Gli oggetti di un tipo particolare il cui numero è aumentato maggiormente appaiono in cima all'elenco (ordinati in base alla colonna **Diff. conteggio**).

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a>Compilazioni di rilascio dei profili senza il debuggerProfile release builds without the debugger

Gli strumenti di profilatura come Utilizzo CPU e Utilizzo memoria possono essere usati con il debugger (vedere le sezioni precedenti) oppure è possibile eseguire gli strumenti di profilatura per la relazione finale con il profiler delle prestazioni, progettato per l'analisi delle build di **rilascio**. Nel profiler delle prestazioni è possibile raccogliere informazioni di diagnostica durante l'esecuzione dell'applicazione e quindi esaminare le informazioni raccolte dopo l'interruzione dell'applicazione. Per altre informazioni sui diversi approcci, vedere [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Ulteriori strumenti, ad esempio lo [strumento .NET Object Allocation,](../profiling/dotnet-alloc-tool.md) sono disponibili anche in Performance Profiler.

![Profiler prestazioni](../profiling/media/prof-tour-performance-profiler.png "Profiler prestazioni")

Aprire Performance Profiler scegliendo **Debug** > **Performance Profiler**.

La finestra consente di selezionare più strumenti di profilatura in alcuni scenari. Gli strumenti come Utilizzo CPU possono visualizzare dati complementari che agevolano l'analisi. È inoltre possibile utilizzare il [profiler della riga di comando](../profiling/profile-apps-from-command-line.md) per abilitare scenari che coinvolgono più strumenti di profilatura.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Esaminare le prestazioni dell'interfaccia utente e gli eventi di accessibilità (piattaforma UWP)

Nelle app UWP è possibile abilitare **Analisi interfaccia utente** nella finestra Strumenti di **diagnostica.** Lo strumento cerca i comuni problemi di prestazioni o accessibilità e li indica nella visualizzazione **Eventi** durante il debug. Le descrizioni degli eventi contengono informazioni che possono essere utili per risolvere i problemi.

![Visualizzare gli eventi di analisi dell'interfaccia utente negli strumenti di diagnosticaView UI analysis events in the diagnostic tools](../profiling/media/prof-tour-ui-analysis.png "Strumenti di diagnostica Visualizza eventi di analisi dell'interfaccia utente")

## <a name="analyze-resource-consumption-xaml"></a>Analizzare l'uso di risorse (XAML)

Nelle app XAML, ad esempio le app WPF desktop di Windows e le app UWP, è possibile analizzare il consumo di risorse usando lo strumento Sequenza temporale applicazione. È possibile ad esempio analizzare il tempo impiegato dall'applicazione per preparare i frame dell'interfaccia utente (layout e rendering), per soddisfare le richieste di rete e disco e in scenari come l'avvio dell'applicazione, il caricamento delle pagine e il ridimensionamento di Windows. Per usare lo strumento, scegliere **Sequenza temporale dell'applicazione** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario con un sospetto problema di consumo delle risorse e quindi scegliere **Arresta raccolta** per generare il report.

I framerate ridotti nel grafico della **velocità effettiva degli elementi visivi** possono corrispondere a problemi di visualizzazione che si riscontrano quando si esegue l'applicazione. Analogamente, i numeri elevati nell'**utilizzo dei thread di interfaccia utente** possono corrispondere a problemi di velocità di risposta dell'interfaccia utente. Nel report è possibile selezionare un periodo di tempo con un sospetto problema di prestazioni e quindi esaminare in dettaglio le attività del thread dell'interfaccia utente nella visualizzazione Dettagli sequenza temporale (riquadro inferiore).

![Strumento di profilatura della sequenza temporale dell'applicazioneApplication Timeline profiling tool](../profiling/media/prof-tour-application-timeline.gif "Sequenza temporale dell'applicazione Tour profilaturaProfiling Tour Application Timeline")

Nella visualizzazione Dettagli sequenza temporale è possibile trovare informazioni quali il tipo di attività (o l'elemento dell'interfaccia utente) insieme alla durata dell'attività. Ad esempio, nella figura un evento **Layout** per un controllo Grid impiega 57,53 ms.

Per altre informazioni, vedere [Sequenza temporale dell'applicazione](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analizzare l'uso della GPU (Direct3D)

Nelle applicazioni Direct3D (i componenti Direct3D devono essere in C++) è possibile esaminare l'attività sulla GPU e analizzare i problemi di prestazioni. Per altre informazioni, vedere l'articolo relativo all'[uso della GPU](/visualstudio/debugger/graphics/gpu-usage). Per usare lo strumento, scegliere **Utilizzo GPU** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che interessa per la profilatura e quindi scegliere **Arresta raccolta** per generare un report.

Quando si seleziona un periodo di tempo nei grafici e si sceglie **Visualizza dettagli**, appare una visualizzazione dettagliata nel riquadro inferiore. Nella visualizzazione dettagliata è possibile esaminare l'entità dell'attività in corso in ogni CPU e GPU. Selezionare gli eventi nel riquadro inferiore per ottenere i popup nella sequenza temporale. Ad esempio, selezionare l'evento **Present** per visualizzare i popup delle chiamate **presenti**. Le linee verticali grigio chiaro di vsync possono essere usate come riferimento per capire se per determinate chiamate **presenti** non è stato eseguito il vsync. Deve esistere una chiamata **presente** tra ogni due vsync affinché l'applicazione esegua costantemente 60 FPS.

![Strumento di profilatura dell'utilizzo della GPU](../profiling/media/prof-tour-gpu-usage.png "Utilizzo GPU Diag")

È anche possibile usare i grafici per determinare se esistono colli di bottiglia delle prestazioni associati alla CPU o GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analizzare le prestazioni (JavaScript UWP)

Per le app UWP è possibile usare lo strumento Memoria JavaScript e lo strumento Velocità di risposta interfaccia utente HTML.

Lo strumento Memoria JavaScript è simile allo strumento Utilizzo memoria disponibile per altri tipi di applicazioni. È possibile usare questo strumento per comprendere in che modo viene usata la memoria e individuare le perdite di memoria nell'applicazione. Per maggiori dettagli sullo strumento, vedere [Memoria JavaScript](../profiling/javascript-memory.md).

![Strumento di profilatura della memoria JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory (Memoria DiagJS)")

Per diagnosticare la velocità di risposta dell'interfaccia utente, i tempi di caricamento lenti e gli aggiornamenti visivi lenti nelle app UWP, usare lo strumento Velocità di risposta interfaccia utente HTML. L'uso è simile a quello dello strumento Sequenza temporale dell'applicazione per altri tipi di applicazioni. Per altre informazioni, vedere [Velocità di risposta dell'interfaccia utente HTML](../profiling/html-ui-responsiveness.md).

![Strumento di profilatura reattività dell'interfaccia utente HTMLHTML UI Responsiveness profiling tool](../profiling/media/diaghtmlresp.png "DiagHTMLResp (informazioni in lingua inlingua fatina del altro gruppo")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analizzare l'uso della rete (piattaforma UWP)

Nelle app UWP è possibile analizzare le operazioni di rete eseguite con l'API `Windows.Web.Http`. Questo strumento può aiutare a risolvere i problemi relativi ad autenticazione e accesso, all'uso non corretto della cache e alle prestazioni insufficienti di visualizzazione download. Per usare lo strumento, scegliere **Rete** nel profiler delle prestazioni e quindi scegliere **Inizia**. Nell'applicazione seguire lo scenario che usa `Windows.Web.Http` e quindi scegliere **Arresta raccolta** per generare il report.

![Strumento di profilatura dell'utilizzo della rete](../profiling/media/prof-tour-network-usage.png "Utilizzo della rete Diag")

Selezionare un'operazione nella visualizzazione di riepilogo per visualizzare altri dettagli.

![Informazioni dettagliate nello strumento Utilizzo rete](../profiling/media/prof-tour-network-usage-details.png "Dettagli sull'utilizzo della rete Diag")

Per altre informazioni, vedere [Utilizzo della rete](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analizzare le prestazioni (strumenti legacy)

::: moniker range="vs-2017"
Se sono necessarie funzionalità, ad esempio la strumentazione, che non sono attualmente presenti negli strumenti Utilizzo CPU o Utilizzo memoria e si eseguono applicazioni desktop o ASP.NET, è possibile usare Esplora prestazioni per la profilatura. Lo strumento non è supportato nelle app UWP. Per altre informazioni, vedere [Esplora prestazioni](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
In Visual Studio 2019, l'Esplora prestazioni legacy e gli strumenti di profilatura correlati, ad esempio la Creazione guidata prestazioni, sono stati inseriti nel profiler delle prestazioni, che è possibile aprire utilizzando **Debug** > **Performance Profiler**. Nel Profiler prestazioni, gli strumenti di diagnostica disponibili dipendono dalla destinazione scelta e dal progetto di avvio aperto corrente. Lo strumento Utilizzo CPU fornisce la funzionalità di campionamento precedentemente supportata nella Creazione guidata prestazioni. Lo strumento di strumentazione fornisce la funzionalità di profilatura instrumentata (per i conteggi e le durate delle chiamate precise) presente nella Creazione guidata prestazioni. Gli strumenti di memoria aggiuntivi vengono visualizzati anche nel profiler delle prestazioni.
::: moniker-end

![Strumento Esplora prestazioni](../profiling/media/prof-tour-performance-explorer.png "Esplora prestazioni")

## <a name="which-tool-should-i-use"></a>Quale strumento si deve usare?

Nella tabella seguente sono riportati i diversi strumenti offerti da Visual Studio e i diversi tipi di progetto con cui possono essere usati:

::: moniker range=">=vs-2019"
|Strumento di prestazioni|Desktop di Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Utilizzo CPU](../profiling/cpu-usage.md)|sì|sì|sì|
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|
|[Allocazione di oggetti .NET](../profiling/dotnet-alloc-tool.md)|yes (solo .NET)|sì|sì|
|[Utilizzo GPU](/visualstudio/debugger/graphics/gpu-usage)|sì|sì|no|
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|sì|sì|no|
|[PerfTips](../profiling/perftips.md)|sì|Sì per XAML, no per HTML|sì|
|[Esplora prestazioni](../profiling/performance-explorer.md)|sì|no|sì|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
::: moniker-end

::: moniker range="vs-2017"
|Strumento di prestazioni|Desktop di Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Utilizzo CPU](../profiling/cpu-usage.md)|sì|sì|sì|
|[Utilizzo memoria](../profiling/memory-usage.md)|sì|sì|sì|
|[Utilizzo GPU](/visualstudio/debugger/graphics/gpu-usage)|sì|sì|no|
|[Sequenza temporale applicazione](../profiling/application-timeline.md)|sì|sì|no|
|[PerfTips](../profiling/perftips.md)|sì|Sì per XAML, no per HTML|sì|
|[Esplora prestazioni](../profiling/performance-explorer.md)|sì|no|sì|
|[IntelliTrace](../debugger/intellitrace.md)|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|Solo .NET con Visual Studio Enterprise|
|[Utilizzo rete](../profiling/network-usage.md)|no|sì|no|
|[Reattività dell'interfaccia utente HTML](../profiling/html-ui-responsiveness.md)|no|Sì per HTML, no per XAML|no|
|[Memoria JavaScript](../profiling/javascript-memory.md)|no|Sì per HTML, no per XAML|no|
::: moniker-end


## <a name="see-also"></a>Vedere anche
- [Debug in Visual Studio](../debugger/debugger-feature-tour.md)
