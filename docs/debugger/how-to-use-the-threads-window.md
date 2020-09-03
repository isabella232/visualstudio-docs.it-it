---
title: Eseguire il debug di un'app multithread
description: Eseguire il debug usando la finestra thread e la barra degli strumenti posizione di debug in Visual Studio
ms.date: 02/14/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33375a8970638765d02a94e6e3e9cd8afc1a0fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348652"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Procedura dettagliata: eseguire il debug di un'app multithread usando la finestra thread (C#, Visual Basic, C++)

Diversi elementi dell'interfaccia utente di Visual Studio consentono di eseguire il debug di app multithread. Questo articolo introduce le funzionalità di debug multithreading nella finestra dell'editor di codice, nella barra degli strumenti **posizione di debug** e nella finestra **thread** . Per informazioni su altri strumenti per il debug di app multithread, vedere [Introduzione al debug di app multithread](../debugger/get-started-debugging-multithreaded-apps.md).

Il completamento di questa esercitazione richiede solo pochi minuti e acquisisce familiarità con le nozioni di base per il debug di app multithread.

## <a name="create-a-multithreaded-app-project"></a>Creare un progetto di app multithread

Creare il progetto di app multithread seguente da usare in questa esercitazione:

1. Aprire Visual Studio e creare un nuovo progetto.

   ::: moniker range=">=vs-2019"

   Se la finestra di avvio non è aperta, **File** scegliere > **finestra di avvio**file.

   Nella finestra Start scegliere **Crea un nuovo progetto**.

   Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Successivamente, scegliere **C#** o **C++** dall'elenco lingua, quindi scegliere **Windows** dall'elenco piattaforma. 

   Dopo aver applicato la lingua e i filtri della piattaforma, scegliere l' **app console (.NET Core)** o, per C++, modello **applicazione console** , quindi scegliere **Avanti**.

   > [!NOTE]
   > Se non viene visualizzato il modello corretto, passare a **strumenti**  >  **Ottieni strumenti e funzionalità...**, che consente di aprire la programma di installazione di Visual Studio. Scegliere il carico di lavoro sviluppo per **desktop .NET** o **sviluppo desktop con C++** , quindi scegliere **modifica**.

   Nella finestra **Configura nuovo progetto** Digitare o immettere *MyThreadWalkthroughApp* nella casella **nome progetto** . Quindi scegliere **Crea**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Dalla barra dei menu in alto scegliere **file**  >  **nuovo**  >  **progetto**. Nel riquadro sinistro della finestra di dialogo **nuovo progetto** scegliere le opzioni seguenti:

   - Per un'app C#, in **Visual c#** scegliere **desktop di Windows**e quindi nel riquadro centrale scegliere **app console (.NET Framework)**.
   - Per un'app C++, in **Visual C++** scegliere **desktop di Windows**, quindi scegliere **applicazione console di Windows**.

   Se non viene visualizzata l' **app console (.NET Core)** o, per C++, il modello di progetto di **app console** , passare a **strumenti**  >  **Ottieni strumenti e funzionalità...**, che consente di aprire la programma di installazione di Visual Studio. Scegliere il carico di lavoro sviluppo per **desktop .NET** o **sviluppo desktop con C++** , quindi scegliere **modifica**.

   Digitare quindi un nome come *MyThreadWalkthroughApp* e fare clic su **OK**.

   Selezionare **OK**.
   ::: moniker-end

   Verrà visualizzato un nuovo progetto console. Una volta creato il progetto, viene visualizzato un file di origine. A seconda della lingua scelta, il file di origine potrebbe essere denominato *Program.cs*, *MyThreadWalkthroughApp. cpp*o *Module1. vb*.

1. Sostituire il codice nel file di origine con il codice di esempio C# o C++ riportato di iniziare a eseguire il [debug di app multithread](../debugger/get-started-debugging-multithreaded-apps.md).

1. Selezionare **file**  >  **Salva tutto**.

## <a name="start-debugging"></a>Consente di iniziare il debug

1. Trovare le righe seguenti nel codice sorgente:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Impostare un punto di interruzione sulla riga facendo clic sulla barra di navigazione `Console.WriteLine();` a sinistra oppure selezionando la riga e premendo **F9**.

   Il punto di interruzione viene visualizzato come un cerchio rosso nella barra di navigazione a sinistra accanto alla riga di codice.

1. Selezionare **debug**  >  **Avvia debug**o premere **F5**.

   L'app viene avviata in modalità di debug e viene sospesa in corrispondenza del punto di interruzione.

1. In modalità di interruzioni aprire la finestra **thread** selezionando **debug**  >  **Windows**  >  **thread**di Windows. Per aprire o visualizzare i **thread** e altre finestre di debug, è necessario essere in una sessione di debug.

## <a name="examine-thread-markers"></a>Esaminare i marcatori dei thread

1. Nel codice sorgente individuare la `Console.WriteLine();` riga.

   1. Fare clic con il pulsante destro del mouse nella finestra **thread** e selezionare **Mostra thread nell'origine** ![Mostra thread in origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dal menu.

   La gronda accanto alla riga del codice sorgente ora Visualizza un ![marcatore del thread](../debugger/media/dbg-thread-marker.png "Marcatore del thread")dell'icona del *marcatore del thread* . Il marcatore del thread indica l'interruzione di un thread in questa posizione. Se è presente più di un thread arrestato nella posizione, viene visualizzata l'icona di ![più thread](../debugger/media/dbg-multithreaded-show-threads.png "thread multipli") .

1. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un DataTip che mostra il nome e il numero ID del thread interrotto. I nomi dei thread possono essere `<No Name>` .

   >[!TIP]
   >Per identificare i thread senza nome, è possibile rinominarli nella finestra **thread** . Fare clic con il pulsante destro del mouse sul thread e scegliere **Rinomina**.

1. Fare clic con il pulsante destro del mouse sul marcatore del thread nel codice sorgente per visualizzare le opzioni disponibili nel menu di scelta rapida.

## <a name="flag-and-unflag-threads"></a>Impostare e rimuovere i flag dei thread

È possibile contrassegnare i thread per tenere traccia dei thread a cui si desidera prestare particolare attenzione.

Flag e Rimuovi i flag dei thread dall'editor del codice sorgente o dalla finestra **thread** . Scegliere se visualizzare solo i thread con flag o tutti i thread dalle barre degli strumenti della finestra dei **thread** o del **percorso di debug** . Le selezioni effettuate da qualsiasi posizione hanno effetto su tutte le posizioni.

### <a name="flag-and-unflag-threads-in-source-code"></a>Contrassegno e Rimuovi flag per i thread nel codice sorgente

1. Aprire la barra degli strumenti **posizione di debug** selezionando **Visualizza**  >  **barra degli strumenti**  >  **posizione di debug**. È anche possibile fare clic con il pulsante destro del mouse sull'area della barra degli strumenti e selezionare **percorso di debug**.

1. La barra degli strumenti **posizione di debug** include tre campi: **processo**, **thread**e **stack frame**. Scorrere l'elenco dei **thread** e notare il numero di thread disponibili. Nell'elenco **thread** il thread attualmente in esecuzione è contrassegnato da un **>** simbolo.

1. Nella finestra del codice sorgente passare il puntatore del mouse sull'icona di un marcatore di thread nella barra di navigazione e selezionare l'icona del flag (o una delle icone di flag vuote) in DataTip. L'icona del flag diventerà rossa.

   È anche possibile fare clic con il pulsante destro del mouse sull'icona di un marcatore del thread, scegliere **flag**, quindi selezionare un thread da contrassegnare dal menu di scelta rapida.

1. Sulla barra degli strumenti **posizione di debug** selezionare l'icona **Mostra solo thread** con flag ![Mostra thread contrassegnati](../debugger/media/dbg-threads-show-flagged.png "Mostra thread con flag")a destra del campo **thread** . L'icona è disabilitata a meno che uno o più thread non siano contrassegnati.

   Solo il thread contrassegnato viene ora visualizzato nell'elenco a discesa **thread** nella barra degli strumenti. Per visualizzare di nuovo tutti i thread, selezionare di nuovo l'icona **Mostra solo thread con flag** .

   >[!TIP]
   >Dopo aver contrassegnato alcuni thread, è possibile posizionare il cursore nell'editor di codice, fare clic con il pulsante destro del mouse e selezionare **Esegui thread contrassegnati su cursore**. Assicurarsi di scegliere il codice che tutti i thread contrassegnati raggiungeranno. **Esegui thread contrassegnati per il cursore** consente di sospendere i thread sulla riga di codice selezionata, semplificando il controllo dell'ordine di esecuzione tramite il [blocco e lo sblocco dei thread](#bkmk_freeze).

1. Per impostare lo stato contrassegnato o non contrassegnato per il thread attualmente in esecuzione, selezionare il pulsante della barra degli strumenti di **attivazione/disattivazione** dei singoli flag, a sinistra del pulsante **Mostra solo thread con flag** . Contrassegnare il thread corrente è utile per individuare il thread corrente quando vengono visualizzati solo i thread con flag.

1. Per rimuovere il flag di un thread, passare il puntatore del mouse sul marcatore del thread nel codice sorgente e selezionare l'icona del flag rosso per cancellarlo oppure fare clic con il pulsante destro del mouse sul marcatore del thread e selezionare **Rimuovi flag**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Flag e Rimuovi i flag dei thread nella finestra thread

Nella finestra **thread** i thread contrassegnati hanno icone di flag rosse accanto, mentre i thread senza flag, se visualizzati, hanno icone vuote.

![Finestra Thread](../debugger/media/dbg-threads-window.png "Finestra Thread")

Selezionare un'icona di contrassegno per impostare lo stato del thread su contrassegnato o senza flag, a seconda dello stato corrente.

È anche possibile fare clic con il pulsante destro del mouse su una riga e selezionare **flag**, Rimuovi **flag**o Rimuovi flag per **tutti i thread** dal menu di scelta rapida.

La barra degli strumenti della finestra **thread** presenta anche un pulsante **Mostra solo thread contrassegnati** , che corrisponde a destra di una delle due icone del flag. Funziona allo stesso modo del pulsante sulla barra degli strumenti **posizione di debug** e uno dei pulsanti controlla la visualizzazione in entrambe le posizioni.

### <a name="other-threads-window-features"></a>Funzionalità della finestra altri thread

Nella finestra **thread** selezionare l'intestazione di una colonna per ordinare i thread in base a tale colonna. Selezionare di nuovo per invertire l'ordinamento. Se vengono visualizzati tutti i thread, se si seleziona la colonna icona flag i thread vengono ordinati in base allo stato contrassegnato o non contrassegnato.

La seconda colonna della finestra **thread** (senza intestazione) è la colonna **thread corrente** . Una freccia gialla in questa colonna contrassegna il punto di esecuzione corrente.

La colonna **location** indica il punto in cui ogni thread viene visualizzato nel codice sorgente. Selezionare la freccia di espansione accanto alla voce **posizione** oppure passare il puntatore del mouse sulla voce per visualizzare uno stack di chiamate parziale per il thread.

>[!TIP]
>Per una visualizzazione grafica degli stack di chiamate per i thread, utilizzare la finestra [stack in parallelo](../debugger/using-the-parallel-stacks-window.md) . Per aprire la finestra, durante il debug, selezionare **debug** >  stack in parallelo di**Windows**  >  **Parallel Stacks**.

Oltre ai **flag**, Rimuovi **flag**e Rimuovi **flag di tutti i thread**, il menu di scelta rapida per gli elementi della finestra dei **thread** è:

- Pulsante **Mostra thread nel codice sorgente** .
- **Visualizzazione esadecimale**, che modifica l' **ID del thread**nella finestra **thread** dal formato decimale in formato esadecimale.
- [Passa a thread](#switch-to-another-thread), che passa immediatamente l'esecuzione a tale thread.
- **Rinominare**, che consente di modificare il nome del thread.
- [Blocca e sblocca](#bkmk_freeze) i comandi.

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Blocca e sblocca l'esecuzione del thread

È possibile bloccare e sbloccare, oppure sospendere e riprendere, i thread per controllare l'ordine in cui i thread eseguono il lavoro. Il blocco e lo sblocco dei thread possono aiutare a risolvere i problemi di concorrenza, ad esempio deadlock e race condition.

> [!TIP]
> Per seguire un singolo thread senza bloccare altri thread, che è anche uno scenario di debug comune, vedere [Introduzione al debug di applicazioni multithread](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Per bloccare e sbloccare i thread:**

1. Nella finestra **thread** fare clic con il pulsante destro del mouse su un thread, quindi scegliere **blocca**. Un'icona di **sospensione** nella colonna **thread corrente** indica che il thread è bloccato.

1. Selezionare le **colonne** nella barra degli strumenti della finestra **thread** , quindi selezionare **numero sospeso** per visualizzare la colonna **numero sospeso** . Il valore del conteggio sospeso per il thread bloccato è **1**.

1. Fare clic con il pulsante destro del mouse sul thread bloccato e selezionare **Sblocca**.

   L'icona di **sospensione** scompare e il valore del **conteggio sospeso** diventa **0**.

## <a name="switch-to-another-thread"></a>Passa a un altro thread

Quando si tenta di passare a un altro thread, è possibile che **l'applicazione si trovi nella finestra modalità di interruzioni** . Questa finestra indica che il thread non dispone di codice che può essere visualizzato dal debugger corrente. Ad esempio, è possibile eseguire il debug di codice gestito, ma il thread è codice nativo. La finestra offre suggerimenti per la risoluzione del problema.

**Per passare a un altro thread:**

1. Nella finestra **thread** prendere nota dell'ID del thread corrente, ovvero il thread con una freccia gialla nella colonna **thread corrente** . È possibile tornare a questo thread per continuare l'applicazione.

1. Fare clic con il pulsante destro del mouse su un thread diverso e selezionare **passa a thread** dal menu di scelta rapida.

1. Osservare che la posizione della freccia gialla è stata modificata nella finestra **thread** . Anche il marcatore del thread corrente originale rimane, come una struttura.

   Esaminare la descrizione comando sul marcatore del thread in Editor origine codice e l'elenco nell'elenco a discesa **thread** nella barra degli strumenti **posizione di debug** . Osservare anche che il thread corrente è stato modificato.

1. Nella barra degli strumenti **posizione di debug** selezionare un thread diverso dall'elenco **thread** . Si noti che il thread corrente cambia anche nelle altre due posizioni.

1. Nell'editor del codice sorgente fare clic con il pulsante destro del mouse su un marcatore del thread, scegliere **passa a thread**, quindi selezionare un altro thread nell'elenco. Osservare che il thread corrente cambia in tutte e tre le posizioni.

Con il marcatore del thread nel codice sorgente, è possibile passare solo a thread interrotti in tale posizione. Con la finestra **Thread** e la barra degli strumenti **Posizione di debug** è possibile passare a tutti i tipi di thread.

A questo punto sono state apprese le nozioni di base per il debug di app multithread. È possibile osservare, contrassegnare e annotare e bloccare e sbloccare i thread utilizzando la finestra **thread** , l'elenco **thread** nella barra degli strumenti **posizione di debug** o i marcatori di thread nell'editor del codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
