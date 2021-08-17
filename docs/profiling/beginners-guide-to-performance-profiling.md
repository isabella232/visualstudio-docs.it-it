---
title: Misurare l'utilizzo della CPU nelle app
description: Analizzare i problemi relativi alle prestazioni della CPU nell'applicazione con gli strumenti di diagnostica integrati nel debugger.
ms.custom: seodec18
ms.date: 04/03/2021
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c13d37683fd724a37cd8688fda87a9e8794ac2c8f480f6022cb76a4ea411260f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369335"
---
# <a name="measure-application-performance-by-analyzing-cpu-usage"></a>Misurare le prestazioni dell'applicazione analizzando l'utilizzo della CPU

Individuare i problemi di prestazioni durante il debug con lo strumento di diagnostica Utilizzo CPU integrato **nel** debugger.  È anche possibile analizzare l'utilizzo della CPU senza un debugger collegato o selezionando come destinazione un'app in esecuzione. Per altre informazioni, vedere [Eseguire gli strumenti di profilatura con o senza il debugger.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

Quando il debugger viene sospeso, lo strumento Utilizzo **CPU** nella finestra di Strumenti di diagnostica raccoglie informazioni sulle funzioni in esecuzione nell'applicazione. Vengono indicate le funzioni che stavano eseguendo un'operazione e un grafico della sequenza temporale consente di concentrarsi su segmenti specifici della sessione di campionamento.

> [!Important]
> Gli strumenti di diagnostica integrati nel debugger sono supportati per lo sviluppo .NET in Visual Studio, tra cui ASP.NET, ASP.NET Core e per lo sviluppo nativo/C++. Il carico di Visual Studio [carico di lavoro](../install/modify-visual-studio.md) corrispondente è obbligatorio. Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Raccogliere i dati di Utilizzo CPU
> * Analizzare i dati d'uso della CPU

Se **Utilizzo CPU** non fornisce i dati necessari, altri strumenti di profilatura nel [Profiler prestazioni](../profiling/profiling-feature-tour.md#post_mortem) forniscono diversi tipi di informazioni che potrebbero essere utili. In molti casi il collo di bottiglia delle prestazioni dell'applicazione può dipendere da un fattore diverso dalla CPU, ad esempio la memoria, il rendering dell'interfaccia utente o il tempo di richiesta di rete.

## <a name="step-1-collect-profiling-data"></a>Passaggio 1: Raccogliere i dati di profilatura

1. Aprire il progetto per cui si vuole eseguire il debug in Visual Studio e impostare un punto di interruzione nell'applicazione in corrispondenza del punto in cui si vuole esaminare l'utilizzo della CPU.

2. Impostare un secondo punto di interruzione alla fine della funzione o dell'area di codice da analizzare.

    Impostando i due punti di interruzione è possibile limitare la raccolta dei dati per le parti di codice che si vuole analizzare.

3. La **Strumenti di diagnostica** viene visualizzata automaticamente, a meno che non sia stata disattivata. Per visualizzare nuovamente la finestra, fare clic su  >  **Debug Windows** Mostra  >  **Strumenti di diagnostica**.

4. È possibile scegliere se visualizzare **Utilizzo CPU**, [Utilizzo memoria](../profiling/Memory-Usage.md) o entrambi usando l'impostazione **Seleziona strumenti** della barra degli strumenti. Se si esegue Visual Studio Enterprise, è anche possibile abilitare o disabilitare IntelliTrace **in** Strumenti  >  **Opzioni**  >  **IntelliTrace**.

     ![Mostra strumenti di diagnostica](../profiling/media/diag-tools-select-tool.png "DiagToolsSelectTool")

     In questa sede ci si occupa principalmente dell'utilizzo della CPU, quindi verificare che l'opzione **Utilizzo CPU** è abilitata (è abilitata per impostazione predefinita).

5. Fare **clic su Debug**  >  **Avvia** debug (o Avvia sulla barra degli strumenti o **F5).** 

     Al termine del caricamento dell'applicazione viene visualizzato il riepilogo degli strumenti di diagnostica. Se è necessario aprire la finestra, fare clic su  >  **Debug Windows** Mostra  >  **Strumenti di diagnostica**.

     ![Scheda Riepilogo strumenti di diagnostica](../profiling/media/diag-tools-summary-tab.png "DiagToolsSummaryTab")

     Per altre informazioni sugli eventi, vedere [Ricerca e filtro nella scheda Eventi della finestra Strumenti di diagnostica eventi](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

6. Eseguire lo scenario in cui viene raggiunto il primo punto di interruzione.

7. Quando il debugger è in pausa, abilitare la raccolta dei dati relativi all'utilizzo della CPU e quindi aprire la scheda **Utilizzo CPU**.

     ![Gli strumenti di diagnostica abilitano la profilatura della CPU](../profiling/media/diag-tools-enable-cpu-profiling.png "DiagToolsEnableCPUProfiling")

     Quando si sceglie **Registra profilo CPU** Visual Studio avvia la registrazione delle funzioni e del tempo necessario per eseguirle. È possibile visualizzare i dati raccolti solo quando l'applicazione viene interrotta in un punto di interruzione.

8. Premere F5 per eseguire l'applicazione fino al secondo punto di interruzione.

     Ora si hanno a disposizione i dati relativi alle prestazioni per l'applicazione, precisamente per l'area di codice compresa tra i due punti di interruzione.

     Il profiler inizia a preparare i dati di thread. Attendere il completamento.

     ![Strumenti di diagnostica - Preparazione dei thread](../profiling/media/diag-tools-preparing-data.png "DiagToolsPreparingThreads")

     Lo strumento Utilizzo CPU consente di visualizzare il report nella scheda **Utilizzo CPU**.

     ![Scheda Utilizzo CPU degli strumenti di diagnostica](../profiling/media/diag-tools-cpu-usage-tab.png "DiagToolsCPUUsageTab")

9. Se si vuole selezionare un'area di codice più specifica da analizzare, selezionare un'area nella sequenza temporale della CPU (deve essere un'area con dati di profilatura).

     ![Strumenti di diagnostica - Selezione di un intervallo di tempo](../profiling/media/diag-tools-select-time-segment.png "DiagToolsSelectTimeSegment")

     A questo punto, è possibile iniziare ad analizzare i dati.

     > [!TIP]
     >  Quando si tenta di identificare i problemi di prestazioni, eseguire più misurazioni. Le prestazioni variano naturalmente da esecuzione a esecuzione e i percorsi del codice vengono in genere eseguiti più lentamente alla prima esecuzione a causa di operazioni di inizializzazione una sola volta, ad esempio il caricamento di DLL, i metodi di compilazione JIT e l'inizializzazione delle cache. Prendendo più misurazioni, si ottiene un'idea migliore dell'intervallo e della mediana della metrica visualizzata, che consente di confrontare la prima volta con le prestazioni dello stato stabile di un'area di codice.

## <a name="step-2-analyze-cpu-usage-data"></a>Passaggio 2: Analizzare i dati di utilizzo della CPU

È consigliabile iniziare ad analizzare i dati esaminando l'elenco di funzioni in Utilizzo CPU, identificando le funzioni che svolgono la maggior parte del lavoro e quindi concentrandosi su ognuna di esse.

1. Nell'elenco delle funzioni esaminare le funzioni che eseguono il maggior numero di operazioni.

    ![Elenco delle funzioni di utilizzo cpu degli strumenti di diagnostica](../profiling/media/diag-tools-cpu-usage-function-list.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > Le funzioni sono elencate in ordine a partire da quelle che svolgono la maggior parte del lavoro (non sono in ordine di chiamata). Ciò consente di identificare rapidamente le funzioni in esecuzione da più tempo.

2. Nell'elenco delle funzioni fare doppio clic su una delle funzioni dell'applicazione che esegue molte operazioni.

    Quando si fa doppio clic su una funzione viene aperta la visualizzazione **Chiamante/Chiamato** nel riquadro a sinistra.

    ![Visualizzazione Chiamante/chiamato in Strumenti di diagnostica](../profiling/media/diag-tools-caller-callee.png "DiagToolsCallerCallee")

    In questa visualizzazione la funzione selezionata viene visualizzata nell'intestazione e nella casella **Funzione corrente** (GetNumber, in questo esempio). La funzione che ha chiamato la funzione corrente viene visualizzata a sinistra, in **Funzioni chiamanti**, e tutte le funzioni chiamate dalla funzione corrente sono riportate nella casella **Funzioni chiamate** sulla destra. Selezionare una delle due caselle per modificare la funzione corrente.

    Questa visualizzazione indica il tempo totale (ms) e la percentuale del tempo complessivo di esecuzione dell'applicazione dedicato al completamento della funzione.
    **Corpo funzione** indica anche la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. In questo esempio 2367 su 2389 ms sono stati usati nel corpo della funzione e i 22 ms rimanenti nel codice esterno chiamato dalla funzione.

    > [!TIP]
    > Valori elevati in **Corpo funzione** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

3. Per una visualizzazione più generale che mostra l'ordine di chiamata delle funzioni, selezionare **Albero delle chiamate** nell'elenco a discesa nella parte superiore del riquadro.

    Ogni area numerata nella figura si riferisce a un passaggio della procedura.

    ::: moniker range=">=vs-2019"
    ![Albero delle chiamate degli strumenti di diagnostica](../profiling/media/vs-2019/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Albero delle chiamate degli strumenti di diagnostica](../profiling/media/diag-tools-call-tree.png "DiagToolsCallTree")
    ::: moniker-end

    |Immagine|Descrizione|
    |-|-|
    |![Passaggio 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|Il nodo di livello principale nell'albero delle chiamate di Utilizzo CPU è uno pseudo-nodo|
    |![Passaggio 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|Nella maggior parte delle app, quando l'opzione [Mostra codice esterno](#view-external-code) è disabilitata, il nodo di secondo livello è un nodo **[Codice esterno]** contenente il codice di sistema e di framework che avvia e arresta l'app, disegna l'interfaccia utente, controlla la pianificazione dei thread e fornisce altri servizi di basso livello all'app.|
    |![Passaggio 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|Gli elementi figlio del nodo di secondo livello sono i metodi del codice utente e le routine asincrone che vengono chiamati o creati dal codice di sistema o di framework di secondo livello.|
    |![Passaggio 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|I nodi figlio di un metodo contengono i dati solo per le chiamate del metodo padre. Quando l'opzione **Mostra codice esterno** è disabilitata, i metodi dell'app possono contenere anche un nodo **[Codice esterno]** .|

    Di seguito sono riportate altre informazioni sui valori di colonna:

    - **CPU totale** indica la quantità di lavoro svolta dalla funzione e dalle funzioni chiamate dalla funzione. Valori elevati di CPU totale indicano le funzioni più dispendiose in generale.

    - **CPU auto** indica la quantità di operazioni eseguite dal codice nel corpo della funzione, escluse quelle eseguite dalle funzioni chiamate dalla funzione. Valori elevati di **CPU auto** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

    - **Moduli** Nome del modulo contenente la funzione o numero dei moduli contenenti le funzioni in un nodo [Codice esterno].

    ::: moniker range=">=vs-2019"
    Per visualizzare le chiamate di funzioni che usano la percentuale massima della CPU nella visualizzazione dell'albero delle chiamate, fare clic su **Espandi percorso critico**.

    ![Percorso critico degli strumenti di diagnostica](../profiling/media/vs-2019/diag-tools-hot-path.png "DiagToolsHotPath")
    ::: moniker-end

    > [!NOTE]
    > Se nell'albero delle chiamate sono presenti porzioni di codice contrassegnate come codice "danneggiato" o "stack unwalkable", è probabile che siano stati eliminati eventi ETW (Event Tracing for Windows). Per risolvere il problema, provare a raccogliere nuovamente la stessa traccia.

## <a name="view-external-code"></a>Visualizzare codice esterno

Il codice esterno rappresenta funzioni nei componenti del sistema e del framework che vengono eseguite dal codice scritto. Include funzioni che avviano e arrestano l'app, disegnano l'interfaccia utente, controllano il threading e forniscono altri servizi di basso livello all'app. Nella maggior parte dei casi il codice esterno è poco interessante, per questo motivo lo strumento Utilizzo CPU raccoglie le funzioni esterne di un metodo utente in un unico nodo **[Codice esterno]** .

Per visualizzare i percorsi delle chiamate del codice esterno, scegliere **Mostra codice esterno** dall'elenco **Visualizzazione filtro** e quindi scegliere **Applica**.

![Scegliere Visualizzazione filtro, quindi Mostra codice esterno](../profiling/media/diag-tools-show-external-code.png "DiagToolsShowExternalCode")

Tieni presente che numerose catene di chiamate del codice esterno sono molto annidate, pertanto la larghezza della colonna Nome funzione può superare la larghezza di visualizzazione in quasi tutti i monitor, ad eccezione di quelli più grandi. In questo caso, i nomi delle funzioni vengono visualizzati **come [...]**.

Usare la casella di ricerca per trovare un nodo che si sta cercando, quindi usare la barra di scorrimento orizzontale per visualizzare i dati.

> [!TIP]
> Se si profila il codice esterno che chiama le funzioni di Windows, è necessario verificare di avere i file con estensione *pdb* più aggiornati. Senza questi file, le visualizzazioni dei rapporti elencherà i nomi delle funzioni di Windows enigmatici e difficile da comprendere. Per altre informazioni su come assicurarsi di disporre dei file necessari, vedere Specificare i file di simboli (con estensione [pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e di origine nel debugger.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come raccogliere e analizzare i dati d'uso della CPU. Se è già stata completata la [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md), è possibile vedere come analizzare l'utilizzo della memoria nelle proprie app.

> [!div class="nextstepaction"]
> [Profilare l'utilizzo della memoria in Visual Studio](../profiling/memory-usage.md)
