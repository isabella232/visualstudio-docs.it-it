---
title: Misurare l'utilizzo della memoria nelle app
description: È possibile rilevare perdite di memoria e memoria inefficiente mentre si sta eseguendo il debug con lo strumento di diagnostica integrato nel debugger.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 801af259243a67b7c41d23abad501ba32b351406
ms.sourcegitcommit: f71a0db01bd4f24521cee5da926b9db3571ddecd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123459155"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Misurare l'utilizzo della memoria in Visual Studio

È possibile rilevare perdite di memoria e memoria inefficiente mentre si sta eseguendo il debug con lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo per comprendere meglio l'impatto sull'utilizzo della memoria dei tipi di oggetti. È anche possibile analizzare l'utilizzo della memoria senza un debugger collegato o selezionando come destinazione un'app in esecuzione. Per altre informazioni, vedere [Eseguire gli strumenti di profilatura con o senza il debugger.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

Anche se è possibile raccogliere snapshot di memoria in qualsiasi momento nello strumento **Utilizzo memoria** è possibile usare il debugger di Visual Studio per controllare la modalità di esecuzione dell'applicazione durante l'analisi dei problemi di prestazioni. L'impostazione dei punti di interruzione, l'esecuzione di istruzioni, l'azione Interrompi tutto e altre azioni del debugger consentono di concentrare l'analisi delle prestazioni sui percorsi del codice più rilevanti. L'esecuzione di tali azioni durante l'esecuzione dell'app può eliminare il rumore dal codice che non interessa l'utente e può ridurre notevolmente la quantità di tempo necessaria per la diagnosi di un problema.

> [!Important]
> Gli strumenti di diagnostica integrati nel debugger sono supportati per lo sviluppo .NET in Visual Studio, incluse le app ASP.NET, ASP.NET Core, native/C++ e le app in modalità mista (.NET e native). Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Creare snapshot della memoria
> * Analizzare i dati di utilizzo della memoria

Se **l'utilizzo** della memoria non fornisce i dati necessari, altri strumenti di profilatura nel [Profiler prestazioni](../profiling/profiling-feature-tour.md#post_mortem) forniscono diversi tipi di informazioni che potrebbero essere utili. In molti casi, il collo di bottiglia delle prestazioni dell'applicazione può essere causato da un elemento diverso dalla memoria, ad esempio CPU, interfaccia utente di rendering o tempo di richiesta di rete.

> [!NOTE]
> **Supporto allocatore personalizzato** Il profiler di memoria nativa funziona raccogliendo i dati [degli eventi ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) di allocazione generati durante la fase di esecuzione.  Gli allocatori in CRT e Windows SDK sono stati annotati a livello di origine in modo che sia possibile acquisirne i dati di allocazione. Nella scrittura degli allocatori, fare in modo che qualsiasi funzione che restituisce un puntatore alla memoria heap appena allocata possa essere decorata con [__declspec](/cpp/cpp/declspec)(allocator), come illustrato in questo esempio per myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

## <a name="collect-memory-usage-data"></a>Raccogliere i dati sull'utilizzo della memoria

1. Aprire il progetto per cui si vuole eseguire il debug in Visual Studio e impostare un punto di interruzione nell'app in corrispondenza del punto in cui si vuole iniziare a esaminare l'utilizzo della memoria.

    Se è presente un'area in cui si sospetta un problema di memoria, impostare il primo punto di interruzione prima che si verifichi tale problema.

    > [!TIP]
    > Poiché può essere difficile acquisire il profilo di memoria di un'operazione specifica quando l'app alloca e dealloca spesso la memoria, impostare punti di interruzione all'inizio e alla fine dell'operazione o eseguire i vari passaggi dell'operazione per trovare il punto esatto in cui l'utilizzo della memoria è cambiato.

2. Impostare un secondo punto di interruzione alla fine della funzione o dell'area di codice da analizzare o dopo un problema di utilizzo sospetto della memoria.

3. La **Strumenti di diagnostica** visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare nuovamente la finestra, fare clic su **Debug**  >  **Windows**  >  **Mostra Strumenti di diagnostica**.

4. Scegliere **Utilizzo memoria** con l'impostazione **Seleziona strumenti** sulla barra degli strumenti.

     ![Mostra strumenti di diagnostica](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Fare clic su **Debug / Avvia debug** (o **Avvia** sulla barra degli strumenti o **F5**).

     Al termine del caricamento dell'applicazione viene visualizzato il riepilogo degli strumenti di diagnostica.

     ![Scheda Riepilogo strumenti di diagnostica](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Poiché la raccolta di dati può influire sulle prestazioni di debug delle app native o in modalità mista, gli snapshot di memoria sono disattivati per impostazione predefinita. Per abilitare gli snapshot in app native o in modalità mista, avviare una sessione di debug (tasto di scelta rapida: **F5**). Quando viene **Strumenti di diagnostica** finestra di dialogo, scegliere la **scheda Utilizzo** memoria e quindi scegliere **Profilatura heap**.
     >
     >  ![Abilitare gli snapshot](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Arresta (tasto di scelta rapida: + **MAIUSC F5)** e riavvia il debug.

6. Per creare uno snapshot all'inizio della sessione di debug, scegliere **Crea snapshot** sulla barra degli strumenti di riepilogo **Utilizzo memoria**. Può essere utile impostare anche qui un punto di interruzione.

    ![Creare uno snapshot](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Per creare una linea di base per i confronti di memoria, si consiglia di creare uno snapshot all'inizio di una sessione di debug.

6. Eseguire lo scenario in cui viene raggiunto il primo punto di interruzione.

7. Quando il debugger viene messo in pausa in corrispondenza del primo punto di interruzione, scegliere **Crea snapshot** sulla barra degli strumenti di riepilogo **Utilizzo memoria**.

8. Premere **F5** per eseguire l'applicazione fino al secondo punto di interruzione.

9. A questo punto, creare un altro snapshot.

     A questo punto, è possibile iniziare ad analizzare i dati.

## <a name="analyze-memory-usage-data"></a>Analizzare i dati di utilizzo della memoria
Nelle righe della tabella di riepilogo Utilizzo memoria sono elencati gli snapshot creati durante la sessione di debug e sono disponibili collegamenti a visualizzazioni più dettagliate.

![Tabella di riepilogo della memoria](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Il nome delle colonne dipende dalla modalità di debug selezionata nelle proprietà del progetto: .NET, nativa o mista (nativa e .NET).

- Le colonne **Oggetti (diff)** e **Allocazioni (diff)** visualizzano il numero di oggetti nella memoria .NET e nativa quando è stato creato lo snapshot.

- La colonna **Dimensioni heap (diff)** visualizza il numero di byte negli heap nativi e .NET

Quando si eseguono più snapshot, le celle della tabella di riepilogo includono la modifica del valore tra lo snapshot della riga e lo snapshot precedente.

Per analizzare l'utilizzo della memoria, fare clic su uno dei collegamenti che consente di visualizzare un report dettagliato dell'utilizzo della memoria:

- Per visualizzare i dettagli della differenza tra lo snapshot corrente e quello precedente, scegliere il collegamento di modifica a sinistra della freccia (![Aumento utilizzo memoria](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento dell'utilizzo della memoria")). Una freccia rossa indica un aumento nell'utilizzo della memoria, mentre una freccia verde indica una riduzione.

> [!TIP]
> Per identificare i problemi di memoria più rapidamente, i report diff vengono ordinati in base ai tipi di oggetto che sono aumentati maggiormente in termini di numero (fare clic sul collegamento di modifica nella colonna **Oggetti (diff)**) o di dimensioni complessive dell'heap (fare clic sul collegamento di modifica nella colonna **Dimensioni heap (diff)**).

- Per visualizzare i dettagli relativi solo allo snapshot selezionato, fare clic sul collegamento non di modifica.

   Il report verrà visualizzato in una finestra separata.

### <a name="managed-types-reports"></a>Report di tipi gestiti
 Scegliere il collegamento corrente di **una cella Oggetti (Diff)** o Allocazioni **(Diff)** nella tabella di riepilogo Utilizzo memoria.

 ![Report dei tipi gestiti dal debugger &#45; percorsi alla radice](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Il riquadro superiore mostra il numero e la dimensione dei tipi dello snapshot, inclusa la dimensione di tutti gli oggetti cui fa riferimento il tipo (**Dimensione inclusiva**).

 L'albero **Percorsi della radice** del riquadro inferiore mostra gli oggetti che fanno riferimento al tipo selezionato nel riquadro superiore. Il Garbage Collector di .NET pulisce la memoria per un oggetto solo quando è stato rilasciato l'ultimo tipo che fa riferimento a tale oggetto.

 **Nell'albero Oggetti** a cui si fa riferimento vengono visualizzati i riferimenti contenuti nel tipo selezionato nel riquadro superiore.

 ![Visualizzazione report degli oggetti a cui si fa riferimento gestito](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Per visualizzare le istanze di un tipo selezionato nel riquadro superiore, scegliere ![l'icona Icona Istanza.](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon")

 ![Screenshot della visualizzazione Istanze nello strumento Visual Studio utilizzo memoria, che mostra il riquadro Istanze e il riquadro Percorsi della radice e oggetti a cui si fa riferimento.](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 La visualizzazione **Istanze** mostra le istanze dell'oggetto selezionato nello snapshot nel riquadro superiore. I riquadri **Percorsi della radice** e **Oggetti a cui si fa riferimento** mostrano gli oggetti che fanno riferimento all'istanza selezionata e i tipi a cui fa riferimento l'istanza selezionata. Quando il debugger viene arrestato nel punto in cui è stato creato lo snapshot, è possibile passare il mouse sulla cella **Valore** per visualizzare i valori dell'oggetto in una descrizione comando.

### <a name="native-type-reports"></a>Report di tipo nativo
 Scegliere il collegamento corrente di una cella **Allocazioni (Diff)** o Dimensioni heap **(Diff)** nella tabella di riepilogo Utilizzo memoria della **finestra Strumenti di diagnostica** memoria.

 ![Visualizzazione di tipo nativo](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 La **Visualizzazione Tipi** mostra il numero e la dimensione dei tipi dello snapshot.

- Scegliere l'icona delle![istanze](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")( Icona dell'istanza nella colonna Tipo di oggetto ) di un tipo selezionato per visualizzare informazioni sugli oggetti del tipo selezionato nello snapshot.

     La visualizzazione **Istanze** mostra ogni istanza del tipo selezionato. La selezione di un'istanza consente di visualizzare lo stack di chiamate che ha comportato la creazione dell'istanza nel riquadro **Stack di chiamate allocazione** .

     ![Screenshot della visualizzazione Istanze nello strumento Visual Studio memoria, che mostra il riquadro Istanze e il riquadro Stack di chiamate di allocazione.](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Scegliere **Visualizzazione stack** dall'elenco **Modalità di visualizzazione** per visualizzare lo stack di allocazione per il tipo selezionato.

     ![Visualizzazione stack](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Report di modifica (Diff)

- Scegliere il collegamento di modifica in una cella della tabella di riepilogo della scheda **Utilizzo memoria** nella finestra **Strumenti di diagnostica** .

   ![Scegliere una modifica per &#40;diff&#41; report](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Scegliere uno snapshot dall'elenco **Confronta con** di un report gestito o nativo.

   ![Scegliere uno snapshot dall'elenco Confronta con](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Il report di modifica aggiunge colonne (contrassegnate con **(Diff)**) al report di base che mostra la differenza tra il valore di snapshot di base e lo snapshot di confronto. Ecco un esempio di come potrebbe apparire un report delle differenze di visualizzazione del tipo nativo:

![Visualizzazione delle diff dei tipi nativi](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blog e video

[Analizzare CPU e memoria in fase di debug](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Memory Profiling in Visual C++ 2015 (Blog di Visual C++ 2015)](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere e analizzare i dati d'uso della memoria. Se è già stato completata la [presentazione del profiler](../profiling/profiling-feature-tour.md), è possibile vedere come analizzare l'uso della CPU nelle app di Windows.

> [!div class="nextstepaction"]
> [Analizzare l'utilizzo della CPU](../profiling/beginners-guide-to-performance-profiling.md)
