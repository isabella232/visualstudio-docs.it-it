---
title: Utilizzo memoria | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0feabad8dfa3b086c9ed5a1a58e231719774f9cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298360"
---
# <a name="memory-usage"></a>Utilizzo memoria
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile rilevare perdite di memoria e memoria inefficiente mentre si sta eseguendo il debug con lo strumento di diagnostica **Utilizzo memoria** integrato nel debugger. Lo strumento Utilizzo memoria consente di eseguire uno o più *snapshot* dell'heap di memoria gestito e nativo. È possibile raccogliere snapshot di app.NET, native o in modalità mista (.NET e native).  
  
- È possibile analizzare un singolo snapshot per ottenere informazioni sull'impatto relativo dei tipi di oggetto sull'uso della memoria e per trovare nell'app il codice che usa la memoria in modo non efficiente.  
  
- È anche possibile confrontare (diff) due snapshot di un'app per individuare le aree del codice che provocano l'incremento dell'uso della memoria nel tempo.  
  
  Il grafico seguente mostra la finestra **Strumenti di diagnostica** in Visual Studio 2015 Update 1:  
  
  ![Update1&#45;diagnostica](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
  Anche se è possibile raccogliere snapshot di memoria in qualsiasi momento nello strumento **Utilizzo memoria** è possibile usare il debugger di Visual Studio per controllare la modalità di esecuzione dell'applicazione durante l'analisi dei problemi di prestazioni. L'impostazione dei punti di interruzione, l'esecuzione di istruzioni, l'azione Interrompi tutto e altre azioni del debugger consentono di concentrare l'analisi delle prestazioni sui percorsi del codice più rilevanti. L'esecuzione di tali azioni durante l'esecuzione dell'app può eliminare il rumore dal codice che non interessa l'utente e può ridurre notevolmente la quantità di tempo necessaria per la diagnosi di un problema.  
  
  È inoltre possibile usare lo strumento di memoria all'esterno del debugger. Vedere [Memory Usage without Debugging](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
> **Supporto allocatore personalizzato.** Il profiler della memoria nativo raccoglie dati relativi a eventi [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) di allocazione generati in fase di esecuzione.  Gli allocatori in CRT e Windows SDK sono stati annotati a livello di origine in modo che sia possibile acquisirne i dati di allocazione.  Nella scrittura degli allocatori, fare in modo che qualsiasi funzione che restituisce un puntatore alla memoria heap appena allocata possa essere decorata con [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(allocator), come illustrato in questo esempio per myMalloc:  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analizzare l’uso della memoria con il debugger  
  
> [!NOTE]
> Poiché la raccolta di dati può influire sulle prestazioni di debug delle app native o in modalità mista, gli snapshot di memoria sono disattivati per impostazione predefinita. Per abilitare app native o in modalità mista di snapshot, avviare una sessione di debug (tasto di scelta rapida: **F5**). Quando la finestra **Strumenti di diagnostica** verrà visualizzata, scegliere la scheda Utilizzo memoria e quindi scegliere **Abilita snapshot**.  
>   
> ![Abilita snapshot](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> Arrestare (tasto di scelta rapida: **MAIUSC + F5**) e riavviare il debug.  
  
 Ogni volta che si vuole acquisire lo stato della memoria, scegliere **Crea snapshot** nella barra degli strumenti del riepilogo **Utilizzo memoria** .  
  
 ![Creazione Snapshot](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Per creare una linea di base per i confronti di memoria, si consiglia di creare uno snapshot all'inizio di una sessione di debug.  
>   - Poiché può essere difficile acquisire il profilo di memoria di un'operazione di proprio interesse quando l'app alloca e dealloca spesso la memoria, impostare punti di interruzione all'inizio e alla fine dell'operazione o eseguire l'operazione per trovare il punto esatto in cui è stata modificata la memoria.  
  
## <a name="viewing-memory-snapshot-details"></a>Visualizzazione dei dettagli dello snapshot di memoria  
 Nelle righe della tabella di riepilogo Utilizzo memoria sono elencati gli snapshot creati durante la sessione di debug.  
  
 Le colonne della riga dipendono dalla modalità di debug scelta nelle proprietà del progetto: .NET, nativa o mista (nativa e .NET).  
  
- Le colonne **Oggetto gestito**e **Allocazioni native** visualizzano il numero di oggetti nella memoria .NET e nativa quando è stato creato lo snapshot.  
  
- Le colonne **Dimensione heap gestito** e **Dimensione heap nativo** visualizzano il numero di byte negli heap .NET e nativi.  
  
- Quando si eseguono più snapshot, le celle della tabella di riepilogo includono la modifica del valore tra lo snapshot della riga e lo snapshot precedente.  
  
   ![Cella della tabella di riepilogo della memoria](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Per visualizzare un report dettagliato:**  
  
- Per visualizzare i dettagli solo dello snapshot selezionato scegliere il collegamento corrente.  
  
- Per visualizzare i dettagli della differenza tra lo snapshot corrente e quello precedente, scegliere il collegamento di modifica.  
  
  Il report verrà visualizzato in una finestra separata.  
  
## <a name="memory-usage-details-reports"></a>Report dettagli di Utilizzo memoria  
  
### <a name="managed-types-reports"></a>Report di tipi gestiti  
 Scegliere il collegamento corrente di una cella **Oggetti gestiti** o **Dimensione heap gestito** nella tabella di riepilogo Utilizzo memoria.  
  
 ![Percorsi del report &#45; di tipo gestito dal debugger alla radice](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Il riquadro superiore mostra il numero e la dimensione dei tipi dello snapshot, inclusa la dimensione di tutti gli oggetti cui fa riferimento il tipo (**Dimensione inclusiva**).  
  
 L'albero **Percorsi della radice** del riquadro inferiore mostra gli oggetti che fanno riferimento al tipo selezionato nel riquadro superiore. Il Garbage Collector di .NET Framework pulisce la memoria per un oggetto solo quando è stato rilasciato l'ultimo tipo cui fa riferimento.  
  
 L'albero **Tipi a cui si fa riferimento** mostra i riferimenti mantenuti dal tipo selezionato nel riquadro superiore.  
  
 ![Visualizzazione report tipi riferimento gestiti](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Per visualizzare le istanze di un tipo selezionato nel riquadro superiore, scegliere l'icona dell' ![icona dell'istanza](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") .  
  
 ![Visualizzazione istanze](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 La visualizzazione **Istanze** mostra le istanze dell'oggetto selezionato nello snapshot nel riquadro superiore. I riquadri Percorsi della radice e Oggetti a cui si fa riferimento mostrano gli oggetti che fanno riferimento all'istanza selezionata e i tipi cui fa riferimento l'istanza selezionata. Quando il debugger viene interrotto nel punto in cui è stato creato lo snapshot, è possibile passare il mouse sulla cella Valore per visualizzare i valori dell'oggetto in una descrizione comando.  
  
### <a name="native-type-reports"></a>Report di tipo nativo  
 Scegliere il collegamento corrente di una cella **Allocazioni native** o **Dimensione heap nativo** della tabella di riepilogo Utilizzo memoria della finestra **Strumenti di diagnostica** .  
  
 ![Visualizzazione del tipo nativo](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 La **Visualizzazione Tipi** mostra il numero e la dimensione dei tipi dello snapshot.  
  
- Scegliere l'icona delle istanze (![icona dell'istanza nella colonna tipo di oggetto](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) di un tipo selezionato per visualizzare le informazioni sugli oggetti del tipo selezionato nello snapshot.  
  
     La visualizzazione **Istanze** mostra ogni istanza del tipo selezionato. La selezione di un'istanza consente di visualizzare lo stack di chiamate che ha comportato la creazione dell'istanza nel riquadro **Stack di chiamate allocazione** .  
  
     ![Visualizzazione istanze](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- Scegliere **Visualizzazione stack** dall'elenco **Modalità di visualizzazione** per visualizzare lo stack di allocazione per il tipo selezionato.  
  
     ![Visualizzazione stack](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Report di modifica (Diff)  
  
- Scegliere il collegamento di modifica in una cella della tabella di riepilogo della scheda **Utilizzo memoria** nella finestra **Strumenti di diagnostica** .  
  
   ![Scegliere un report &#40;di&#41;modifica dif f](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Scegliere uno snapshot dall'elenco **Confronta con** di un report gestito o nativo.  
  
   ![Scegliere uno snapshot dall'elenco Confronta con](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Il report di modifica aggiunge colonne (contrassegnate con **(Diff)** ) al report di base che mostra la differenza tra il valore di snapshot di base e lo snapshot di confronto. Ecco un esempio di come potrebbe apparire un report delle differenze di visualizzazione del tipo nativo:  
  
  ![Differenze tra tipi nativi nativi](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blog e video  
 [Diagnostic Tools debugger window in Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/) (Finestra del debugger degli strumenti di diagnostica in Visual Studio 2015)  
  
 [Blog: Strumento di utilizzo della memoria durante il debug in Visual Studio 2015](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Blog su Visual C++: Diagnostica della memoria nativa in Visual Studio 2015 Preview](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Blog su Visual C++: Strumenti di diagnostica della memoria nativa per Visual Studio 2015 CTP](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
