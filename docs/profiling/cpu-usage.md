---
title: Analizzare l'utilizzo della CPU nel Profiler prestazioni
description: Informazioni sullo strumento per le prestazioni Utilizzo CPU, che mostra il tempo e la percentuale di CPU impiegato per l'esecuzione del codice nelle app C++, C#, Visual Basic e JavaScript.
ms.custom: SEO-VS-2020
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2e8db1683fa44ffa75ba6e0ac6aa1a5101c812c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039306"
---
# <a name="analyze-cpu-usage-without-debugging-in-the-performance-profiler"></a>Analizzare l'utilizzo della CPU senza eseguire il debug nel Profiler prestazioni

Un approccio ottimale per avviare l'analisi dei problemi di prestazioni nell'app è l'esame dell'uso della CPU. Lo strumento per le prestazioni **Utilizzo CPU** visualizza il tempo e la percentuale d'uso della CPU dedicati all'esecuzione del codice nelle app C++, C#/Visual Basic e JavaScript.

Lo strumento Utilizzo CPU può essere eseguito in un progetto di Visual Studio aperto, in un'app di Microsoft Store installata oppure può essere collegato a un'app o un processo in esecuzione. È possibile eseguire lo strumento Utilizzo CPU con o senza il debug. Per altre informazioni, vedere [Eseguire gli strumenti di profilatura con o senza il debugger.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

Le istruzioni seguenti illustrano come usare lo strumento Utilizzo CPU senza il debugger, con Profiler prestazioni di Visual Studio. L'esempio usa una build di rilascio in un computer locale. Le build di rilascio offrono la migliore visualizzazione delle prestazioni effettive dell'app. Per analizzare l'utilizzo della CPU con le build di debug (debugger collegato), vedere la Guida per [principianti alla profilatura delle prestazioni.](../profiling/beginners-guide-to-performance-profiling.md)

In genere il computer locale replica in modo ottimale l'esecuzione dell'app installata. Per raccogliere dati da un dispositivo remoto, eseguire l'app direttamente nel dispositivo e non tramite una connessione Desktop remoto.

>[!NOTE]
>Per l'uso di [Profiler prestazioni](../profiling/profiling-feature-tour.md) è necessario Windows 7 o versione successiva.

## <a name="collect-cpu-usage-data"></a>Raccogliere i dati di Utilizzo CPU

1. Nel progetto Visual Studio, impostare la configurazione della soluzione su **Rilascio** e selezionare Debugger Windows **locale** (o **Computer** locale ) come destinazione della distribuzione.

    ![Selezionare Versione e Computer locale](../profiling/media/cpuuse_selectreleaselocalmachine.png "Selezionare Versione e Computer locale")

1. Selezionare **Debug**  >  **Profiler prestazioni**.

1. In **Strumenti disponibili** selezionare **Utilizzo CPU** e quindi selezionare **Avvia**.

    ![Selezionare Utilizzo CPU](../profiling/media/cpuuse_lib_choosecpuusage.png "Selezionare Utilizzo CPU")

4. Dopo l'avvio dell'app viene avviata la sessione di diagnostica e vengono visualizzati i dati d'uso della CPU. Dopo aver completato la raccolta dei dati, selezionare **Arresta raccolta**.

   ![Arrestare la raccolta dati di Utilizzo CPU](../profiling/media/cpu_use_wt_stopcollection.png "Arrestare la raccolta dati di Utilizzo CPU")

   Lo strumento Utilizzo CPU analizza i dati e visualizza il report.

   ![Report utilizzo CPU](../profiling/media/cpu_use_wt_report.png "Report utilizzo CPU")

## <a name="analyze-the-cpu-usage-report"></a>Analizzare il report di Utilizzo CPU

Il report di diagnostica viene ordinato per **CPU totale**, dal valore maggiore al minore. Per modificare l'ordinamento o la colonna di ordinamento, selezionare le intestazioni di colonna. Usare l'elenco a discesa **Filtro** per selezionare o deselezionare i thread da visualizzare e usare la casella **Ricerca** per cercare un thread o un nodo specifico.

::: moniker range=">=vs-2019"
A partire da Visual Studio 2019, è possibile scegliere i pulsanti **Espandi percorso critico** e **Mostra percorso critico** per visualizzare le chiamate di funzione che usano la percentuale massima della CPU nella visualizzazione dell'albero delle chiamate.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> Colonne di dati Utilizzo CPU

|Nome|Descrizione|
|-|-|
|**CPU totale [unità, %]**|![Equazione % dati totali](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Millisecondi e percentuale dell'attività della CPU usata dalle chiamate alla funzione e dalle funzioni chiamate dalla funzione nell'intervallo di tempo selezionato. Il valore è diverso da quello del grafico della sequenza temporale di **Utilizzo CPU**, che confronta l'attività CPU totale dell'app in un intervallo di tempo con la capacità CPU disponibile totale.|
|**CPU auto [unità, %]**|![Equazione % auto](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Millisecondi e percentuale dell'attività della CPU usata dalle chiamate alla funzione nell'intervallo di tempo selezionato, escluse le funzioni chiamate dalla funzione.|
|**Modulo**|Nome del modulo che contiene la funzione.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> Albero delle chiamate di Utilizzo CPU

Per visualizzare l'albero delle chiamate, selezionare il nodo padre nel report. La pagina **Utilizzo CPU** viene aperta con la visualizzazione **Chiamante/chiamato**. Nell'elenco a discesa **Visualizzazione corrente** selezionare **Albero delle chiamate**.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Struttura dell'albero delle chiamate

::: moniker range=">=vs-2019"
![Struttura dell'albero delle chiamate](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Struttura dell'albero delle chiamate")
::: moniker-end
::: moniker range="vs-2017"
![Struttura dell'albero delle chiamate](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Struttura dell'albero delle chiamate")
::: moniker-end

|Immagine|Descrizione|
|-|-|
|![Passaggio 1](../profiling/media/procguid_1.png "ProcGuid_1")|Il nodo di livello principale nell'albero delle chiamate di Utilizzo CPU è uno pseudo-nodo.|
|![Passaggio 2](../profiling/media/procguid_2.png "ProcGuid_2")|Nella maggior parte delle app, quando l'opzione **Mostra codice esterno** opzione è disabilitata il nodo di secondo livello è un nodo **[Codice esterno]**. Il nodo contiene il codice di sistema e di framework che avvia e arresta l'app, disegna l'interfaccia utente, controlla la pianificazione dei thread e offre altri servizi di basso livello all'app.|
|![Passaggio 3](../profiling/media/procguid_3.png "ProcGuid_3")|Gli elementi figlio del nodo di secondo livello sono i metodi del codice utente e le routine asincrone che vengono chiamati o creati dal codice di sistema o di framework di secondo livello.|
|![Passaggio 4](../profiling/media/procguid_4.png "ProcGuid_4")|I nodi figlio di un metodo contengono dati solo per le chiamate del metodo padre. Quando l'opzione **Mostra codice esterno** è disabilitata, i metodi dell'app possono contenere anche un nodo **[Codice esterno]** .|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Codice esterno

Le funzioni di sistema e framework eseguite dal codice sono dette *codice esterno*. Le funzioni codice esterno avviano e arrestano l'app, disegnano l'interfaccia utente, controllano il threading e offre altri servizi di basso livello all'app. Nella maggior parte dei casi il codice esterno non risulta interessante, pertanto l'albero delle chiamate di Utilizzo CPU raccoglie le funzioni esterne di un metodo utente in un unico nodo **[Codice esterno]**.

Per visualizzare i percorsi delle chiamate di codice esterno, nella pagina del report di diagnostica principale (riquadro destro) selezionare **Mostra codice esterno** nell'elenco a discesa **Filtro** e quindi selezionare **Applica**. La visualizzazione **Albero delle chiamate** della pagina **Utilizzo CPU** espande le chiamate al codice esterno. L'elenco a discesa **Filtro** è disponibile nella pagina di diagnostica principale, non nelle visualizzazioni dettagliate.

![Mostra codice esterno](../profiling/media/cpu_use_wt_filterview.png "Mostra codice esterno")

Numerose catene di chiamate del codice esterno sono annidate in profondità, pertanto la larghezza della catena può superare la larghezza di visualizzazione della colonna **Nome funzione**. In questo caso i nomi delle funzioni vengono visualizzati come **...**.

![Codice esterno annidato nell'albero delle chiamate](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Codice esterno annidato nell'albero delle chiamate")

Per trovare il nome di una funzione, usare la casella di ricerca. Passare il mouse sopra la riga selezionata oppure usare la barra di scorrimento orizzontale per visualizzare i dati.

::: moniker range=">=vs-2019"
![Ricerca di codice esterno annidato](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "Ricerca di codice esterno annidato")
::: moniker-end
::: moniker range="vs-2017"
![Ricerca di codice esterno annidato](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Ricerca di codice esterno annidato")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funzioni asincrone nell'albero delle chiamate di utilizzo della CPU

 Quando il compilatore rileva un metodo asincrono, crea una classe nascosta per controllare l'esecuzione del metodo. A livello concettuale la classe è una macchina a stati. La classe dispone di funzioni generate dal compilatore che chiamano in modo asincrono i metodi originali e i callback, l'utilità di pianificazione e gli iteratori necessari per la loro esecuzione. Quando un metodo padre chiama il metodo originale, il compilatore rimuove il metodo dal contesto di esecuzione del metodo padre ed esegue i metodi della classe nascosta nel contesto del codice di sistema e di framework che controlla l'esecuzione dell'app. Spesso, ma non sempre, i metodi asincroni vengono eseguiti in uno o più thread diversi. Il codice è visualizzato nell'albero delle chiamate **Utilizzo CPU** come figlio del nodo **[Codice esterno]** immediatamente sotto il nodo principale dell'albero.

Nell'esempio seguente i primi due nodi sotto **[Codice esterno]** sono i metodi generati dal compilatore della classe macchina a stati. Il terzo nodo è la chiamata al metodo originale.

![Nodo asincrono](media/cpu_use_wt_getmaxnumberasync_selected.png "Nodo asincrono")

Espandere i metodi generati per vedere che cosa accade:

![Nodo asincrono espanso](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Nodo asincrono espanso")

- `MainPage::GetMaxNumberAsyncButton_Click` si limita a gestire un elenco dei valori delle attività, a calcolare il massimo dei risultati e a visualizzare l'output.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` mostra l'attività necessaria per pianificare e avviare le 48 attività che eseguono il wrapping della chiamata a `GetNumberAsync`.

- `MainPage::<GetNumberAsync>b__b` visualizza le operazioni eseguite dalle attività che chiamano `GetNumber`.
