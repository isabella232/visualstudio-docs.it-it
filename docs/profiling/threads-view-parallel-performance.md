---
title: Visualizzazione Thread nel visualizzatore di concorrenza | Microsoft Docs
description: Nella visualizzazione Thread è possibile identificare i thread che eseguono codice durante un segmento di esecuzione.
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9c715267fe002b136ee07e2a925b979437fe97b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141116"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Visualizzazione Thread nel visualizzatore di concorrenza

La visualizzazione **Thread** è la visualizzazione più dettagliata e ricca di funzionalità disponibile nel visualizzatore di concorrenza. Nella visualizzazione **Thread** è possibile identificare i thread che eseguono codice durante un segmento di esecuzione e verificare se i thread stanno eseguendo o bloccando il codice per motivi di sincronizzazione, I/O o di altro tipo. I report della visualizzazione **Thread** inoltre profilano l'esecuzione dell'albero dello stack di chiamate e i thread di sblocco.

Quando i thread sono in esecuzione, il visualizzatore di concorrenza raccoglie campioni. Al termine dell'esecuzione di un thread, il visualizzatore esamina tutti gli eventi di cambio di contesto del sistema operativo per il thread. I cambi di contesto possono verificarsi perché:

- Un thread è bloccato su una primitiva di sincronizzazione.
- Il quantum di un thread scade.
- Un thread esegue una richiesta di I/O di blocco.

Il visualizzatore di concorrenza classifica il thread e gli eventi di cambio di contesto e cerca nello stack di chiamate del thread le API di blocco conosciute. Visualizza le categorie di thread nella legenda attiva in basso a sinistra nella visualizzazione **Thread**. Nella maggior parte dei casi è possibile identificare la causa principale di un evento di blocco esaminando gli stack di chiamate che corrispondono agli eventi di cambio di contesto.

Se non vi è alcuna corrispondenza di stack di chiamate, il visualizzatore di concorrenza usa il motivo dell'attesa indicato da [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Tuttavia, la categoria [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] può essere basata su un dettaglio di implementazione e non riflettere la finalità dell'utente. Ad esempio, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] segnala il motivo dell'attesa per il blocco in lettura-scrittura nativo come I/O anziché come sincronizzazione.

La visualizzazione **Thread** illustra anche le dipendenze tra thread. Ad esempio, se si individua un thread bloccato su un oggetto di sincronizzazione, è possibile trovare il thread che lo ha sbloccato. È possibile esaminare lo stack di chiamate per il thread di sblocco nel punto di cui ha sbloccato l'altro.

È possibile usare la visualizzazione **Thread** per:

- Identificare i motivi per cui l'interfaccia utente di un'app non risponde durante alcune fasi di esecuzione.
- Determinare la quantità di tempo trascorso in un blocco dovuto a sincronizzazione, I/O, errori di pagina e altri eventi.
- Individuare il grado di interferenza da altri processi in esecuzione nel sistema.
- Identificazione dei problemi di bilanciamento del carico per l'esecuzione parallela.
- Trovare i motivi per la scalabilità non ottimale o non esistente. Ad esempio, il motivo per cui le prestazioni di un'app parallela non migliorano quando sono disponibili più core logici.
- Individuazione del livello di concorrenza nell'app, per agevolare la parallelizzazione.
- Identificare le dipendenze tra thread di lavoro e percorsi critici di esecuzione.

## <a name="use-threads-view"></a>Usare la visualizzazione Thread

Per avviare il visualizzatore di concorrenza, selezionare **Analizza**  >  **visualizzatore** di concorrenza e quindi selezionare un'opzione, ad esempio **Avvia nuovo processo**.

Il visualizzatore di concorrenza avvia l'app e raccoglie una traccia finché non si seleziona **Arresta raccolta**. Il visualizzatore quindi analizza la traccia e visualizza i risultati nella pagina del report di traccia.

Selezionare la scheda **Thread** in alto a sinistra nel report per aprire la visualizzazione **Thread**.

![Visualizzazione Thread](../profiling/media/threadsviewnarrowing.png "visualizzazione thread")

Selezionare gli intervalli di tempo e i thread per avviare un'analisi delle prestazioni.

## <a name="timeline-analysis"></a>Analisi della sequenza temporale

La parte superiore della visualizzazione **Thread** è una sequenza temporale. La sequenza temporale indica l'attività di tutti i thread nel processo e di tutti i dispositivi disco fisici nel computer host. Vengono inoltre visualizzati l'attività della GPU e gli eventi marcatori.

L'asse x della sequenza temporale rappresenta il tempo mentre sull'asse y sono riportati diversi canali:

- Due canali di I/O per ogni unità disco del sistema, un canale per la lettura e uno per la scrittura.
- Un canale per ogni thread del processo.
- Canali dei marcatori, se nella traccia sono presenti eventi marcatori. I canali dei marcatori vengono inizialmente visualizzati sotto i canali di thread che hanno generato tali eventi.
- Canali GPU.

Inizialmente i thread sono disposti nell'ordine in cui vengono creati, quindi il thread principale dell'app è il primo. Selezionare un'altra opzione nell'elenco a discesa **Ordina per** e ordinare i thread in base a un altro criterio, ad esempio **Esecuzione**.

I colori della sequenza temporale indicano lo stato di un thread in un determinato momento. I segmenti verdi sono quelli in esecuzione, i segmenti rossi sono bloccati per la sincronizzazione, i segmenti gialli sono quelli con precedenza e i segmenti viola sono impegnati in operazioni di I/O del dispositivo.

È possibile fare zoom avanti per visualizzare altri dettagli oppure zoom indietro per visualizzare un intervallo di tempo più lungo. Selezionare segmenti e punti nel grafico per ottenere dettagli sulle categorie, gli orari di avvio, i ritardi e gli stati dello stack di chiamate.

Usare la sequenza temporale per esaminare il bilanciamento del lavoro tra i thread coinvolti in un ciclo parallelo o in attività simultanee. Se un thread richiede più tempo per il completamento rispetto agli altri, il lavoro potrebbe essere sbilanciato. È possibile migliorare le prestazioni dell'app distribuendo il lavoro in modo più uniforme tra i thread.

Se in un determinato momento solo un thread è in esecuzione, l'app potrebbe non sfruttare completamente la concorrenza nel sistema. È possibile usare il grafico della sequenza temporale per esaminare le dipendenze tra thread e le relazioni temporali tra i thread di blocco e quelli bloccati. Per riordinare i thread, selezionare un thread e quindi l'icona Su o Giù nella barra degli strumenti.

È possibile nascondere i thread che non sono in funzione o sono completamente bloccati perché le relative statistiche sono irrilevanti e potrebbero intasare i rapporti. Per nascondere i thread, selezionarne i nomi e quindi selezionare le icone **Nasconde i thread selezionati** oppure **Nasconde tutto eccetto i thread selezionati** nella barra degli strumenti. Per identificare i thread da nascondere, selezionare il collegamento **Riepilogo per thread** in basso a sinistra. È possibile nascondere i thread senza attività nel grafico **Riepilogo per thread**.

### <a name="thread-execution-details"></a>Dettagli sull'esecuzione dei thread
Per visualizzare informazioni più dettagliate su un segmento di esecuzione, selezionare un punto su un segmento verde della sequenza temporale. Il visualizzatore di concorrenza visualizza un cursore nero sopra il punto selezionato e ne indica lo stack di chiamate nella scheda **Corrente** del riquadro inferiore. È possibile selezionare più punti nel segmento di esecuzione.

>[!NOTE]
>Il visualizzatore di concorrenza potrebbe non essere in grado di risolvere una selezione in un segmento di esecuzione se la durata del segmento è inferiore a un millisecondo.

Per ottenere un profilo di esecuzione per tutti i thread non nascosti nell'intervallo di tempo attualmente selezionato, scegliere **Esecuzione** nella legenda in basso a sinistra.

### <a name="thread-blocking-details"></a>Dettagli sul blocco dei thread
Per ottenere informazioni su una determinata area di un thread, passare il mouse sull'area nella sequenza temporale per visualizzare una descrizione comando, che contiene diverse informazioni, tra cui categoria, ora di inizio e ritardo. Selezionare l'area per visualizzare lo stack di chiamate relativo a quel punto nel tempo nella scheda **Corrente** del riquadro inferiore. Nel riquadro sono indicati anche la categoria, il ritardo, l'API di blocco, se presente, e l'eventuale thread di sblocco. Esaminando lo stack di chiamate, è possibile determinare i motivi sottostanti per gli eventi di blocco del thread.

Un percorso di esecuzione può avere alcuni eventi di blocco. Per esaminarli in base alla categoria di blocco e identificare le aree problematiche più rapidamente, selezionare una categoria di blocco nella legenda a sinistra.

### <a name="dependencies-between-threads"></a>Dipendenze tra thread
Il visualizzatore di concorrenza visualizza le dipendenze tra i thread in modo da stabilire cosa stava tentando di eseguire un thread bloccato e quale altro thread abbia abilitato l'esecuzione.

Per determinare quale thread ha sbloccato un altro thread, selezionare il segmento di blocco nella sequenza temporale. Se il visualizzatore di concorrenza è in grado di determinare il thread di sblocco, disegna una linea tra il thread di sblocco e il segmento di esecuzione che segue il segmento di blocco. Selezionare la scheda **Stack di sblocco** nel riquadro inferiore per visualizzare lo stack di chiamate pertinente.

## <a name="profile-reports"></a>Report dei profili
Il grafico della sequenza temporale che segue è un riquadro con le schede **Rapporto profili**, **Corrente** e **Stack di sblocco** del report. I report si aggiornano automaticamente quando si modifica la selezione della sequenza temporale e dei thread. Per le tracce di grandi dimensioni, il riquadro dei report può essere temporaneamente non disponibile durante il calcolo degli aggiornamenti.

### <a name="profile-report-tab"></a>Scheda Rapporto profili

La scheda **Rapporto profili** ha due filtri:

- Per escludere le voci dell'albero delle chiamate che hanno richiesto un tempo minimo, digitare un valore di filtro compreso tra 0 e 99% nel campo **Riduzione rumore in**. Il valore predefinito è 2%.
- Per visualizzare solo gli alberi delle chiamate per il codice, selezionare la casella di controllo **Just My Code**. Per visualizzare tutti gli alberi delle chiamate, deselezionare la casella di controllo.

La scheda **Rapporto profili** contiene i report per le categorie e i collegamenti nella legenda. Per visualizzare un report, selezionare una delle voci a sinistra:

- **Esecuzione** Il report **Esecuzione** illustra il dettaglio del tempo che l'applicazione ha impiegato nell'esecuzione.

  Per trovare la riga di codice in cui è trascorso il tempo di esecuzione, espandere l'albero delle chiamate e scegliere **Visualizza origine** o **Visualizza siti di chiamata** dal menu di scelta rapida per la voce dell'albero delle chiamate. **Visualizzazione origine** consente di individuare la riga di codice eseguita. **Visualizza siti di chiamata** permette di individuare la riga di codice che ha chiamato la riga eseguita. Se esiste una sola riga di sito di chiamata, viene evidenziato il codice corrispondente. Se esistono diversi siti di chiamata, selezionarne uno nella finestra di dialogo e quindi selezionare **Passa all'origine**. È spesso molto utile individuare il sito di chiamata con il maggior numero di istanze, i tempi più elevati o entrambi. Per altre informazioni, vedere [Report del profilo di esecuzione](../profiling/execution-profile-report.md).

- **Sincronizzazione** Il report **Sincronizzazione** illustra le chiamate responsabili dei blocchi di sincronizzazione, oltre ai tempi di blocco totali di ogni stack di chiamate. Per altre informazioni, vedere [Periodo di sincronizzazione](../profiling/synchronization-time.md).

- **I/O** Il report **I/O** illustra le chiamate responsabili dei blocchi di I/O, oltre ai tempi di blocco totali di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di I/O (visualizzazione Thread)](../profiling/i-o-time-threads-view.md).

- **Sospensione** Il report **Sospensione** illustra le chiamate responsabili dei blocchi di sospensione, oltre ai tempi di blocco totali di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di sospensione](../profiling/sleep-time.md).

- **Gestione della memoria** Il report **Gestione della memoria** illustra le chiamate in cui si sono verificati blocchi di gestione della memoria, oltre ai tempi di blocco totali di ogni stack di chiamate. Usare queste informazioni per identificare le aree che presentano problemi notevoli di paging o di Garbage Collection.  Per altre informazioni, vedere [Tempo di gestione della memoria](../profiling/memory-management-time.md).

- **Precedenza** Il report **Precedenza** indica dove i processi nel sistema hanno avuto la precedenza sul processo corrente e i singoli thread che hanno sostituito i thread del processo corrente. È possibile usare queste informazioni per identificare i processi e i thread maggiormente responsabili della precedenza. Per altre informazioni, vedere [Tempo di precedenza](../profiling/preemption-time.md).

- **Elaborazione interfaccia utente** Il report **Elaborazione interfaccia utente** indica le chiamate responsabili dei blocchi di elaborazione dell'interfaccia utente, oltre ai tempi di blocco totali di ogni stack di chiamate. Per altre informazioni, vedere [Tempo di elaborazione dell'interfaccia utente](../profiling/ui-processing-time.md).

- **Riepilogo per thread** Selezionare **Riepilogo per thread** per visualizzare un grafo che illustra lo stato dei thread per l'intervallo di tempo attualmente selezionato. Le colonne di colori diversi indicano il tempo totale trascorso da ciascun thread nell'esecuzione, nel blocco, nell'I/O e in altri stati. I thread sono etichettati nella parte inferiore. Quando si modifica il livello di zoom nel grafico della sequenza temporale, il grafico viene aggiornato automaticamente.

  Con alcuni livelli di zoom, alcuni thread potrebbero non apparire nel grafico. In questo caso, a destra vengono visualizzati puntini di sospensione (**...**). Se il thread desiderato non è presente, è possibile nascondere gli altri thread. Per altre informazioni, vedere [Report di riepilogo per thread](../profiling/per-thread-summary-report.md).

- **Operazioni su disco** Selezionare **Operazioni su disco** per visualizzare i processi e i thread coinvolti in operazioni di I/O su disco per il processo corrente, i file interessati (ad esempio, le DLL caricate), il numero di byte letti e altre informazioni. È possibile usare questo rapporto per valutare il tempo impiegato per accedere ai file durante l'esecuzione, specialmente se il processo sembra presentare vincoli di I/O. Per altre informazioni, vedere [Report delle operazioni su disco](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Scheda Corrente
Questa scheda mostra lo stack di chiamate per un punto selezionato su un segmento di thread nel grafico della sequenza temporale. Gli stack di chiamate vengono tagliati per visualizzare solo l'attività correlata all'app.

### <a name="unblocking-stack-tab"></a>Scheda Stack di sblocco
Questa scheda indica quale thread ha sbloccato il thread selezionato e lo stack di chiamate di sblocco.

## <a name="see-also"></a>Vedi anche
- [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)
