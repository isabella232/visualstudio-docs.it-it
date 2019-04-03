---
title: Debug di un'app multithread
description: Eseguire il debug usando la finestra thread e la barra degli strumenti posizione di Debug in Visual Studio
ms.date: 11/21/2018
ms.topic: conceptual
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
ms.openlocfilehash: e3a87fd0480727a524b36ab209f5126b0f996c30
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790797"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Procedura dettagliata: Debug di un'app con multithreading usando la finestra thread (C#, Visual Basic, C++)

Diversi elementi dell'interfaccia utente di Visual Studio consentono di eseguire il debug delle App a thread multipli. Questo articolo presenta le funzionalità di debug con multithreading nella finestra editor di codice **posizione di Debug** sulla barra degli strumenti, e **thread** finestra. Per informazioni sugli altri strumenti per il debug di applicazioni multithreading, vedere [iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md).

Il completamento di questa esercitazione richiede solo pochi minuti e consente di acquisire familiarità con le nozioni fondamentali di debug di applicazioni a thread multipli.

## <a name="create-a-multithreaded-app-project"></a>Creare un progetto di app a thread multipli

Creare il progetto di app con multithreading seguenti da usare in questa esercitazione:

1. Aprire Visual Studio e creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **Esc** per chiudere la finestra di avvio. Tipo di **Ctrl + Q** per aprire la casella di ricerca, digitare **console** (o **c + +**), scegliere **modelli**e quindi:

    - Per C#, scegliere **Crea nuovo progetto App Console (.NET Framework)** per C#. Nella finestra di dialogo visualizzata scegliere **Crea**.
    - Per C++, scegliere **Crea nuovo progetto App Console**. Nella finestra di dialogo visualizzata scegliere **Crea**.

    Quindi, digitare un nome simile **MyThreadWalkthroughApp** e fare clic su **crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra di **nuovo progetto** dialogo finestra, scegliere le opzioni seguenti:
    - Per un C# app, sotto **Visual C#** , scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App Console (.NET Framework)**.
    - Per un'app C++, sotto **Visual C++**, scegliere **Windows Desktop**, quindi scegliere **applicazione Console Windows**.

    Quindi, digitare un nome simile **MyThreadWalkthroughApp** e fare clic su **OK**.
    ::: moniker-end

    Se il modello di progetto **App console** non viene visualizzato, passare a **Strumenti** > **Ottieni strumenti e funzionalità...**, aprendo così il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET** o **Sviluppo di applicazioni desktop con C++**, quindi scegliere **Modifica**.

    Verrà visualizzato il nuovo progetto **Esplora soluzioni**, e un file di origine denominata *Program.cs* oppure *MyThreadWalkthroughApp. cpp* viene aperto nella finestra del codice sorgente.

1. Sostituire il codice nel file di origine con il C# o codice di esempio di C++ da [iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md).

1. Selezionare **File** > **Salva tutto**.

## <a name="start-debugging"></a>Avvia debug

1. Trovare le righe seguenti nel codice sorgente:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Impostare un punto di interruzione per il `Console.WriteLine();` riga facendo clic nella barra di navigazione a sinistra, oppure selezionando la riga e premendo **F9**.

   Il punto di interruzione viene visualizzato come un cerchio rosso nella barra di navigazione a sinistra accanto alla riga di codice.

1. Selezionare **Debug** > **Avvia debug**, oppure premere **F5**.

   L'app viene avviata in modalità di debug e si fermerà in corrispondenza del punto di interruzione.

1. In modalità di interruzione, aprire il **thread** finestra selezionando **Debug** > **Windows** > **thread**. È necessario essere in una sessione di debug per aprire o vedere i **thread** e altre finestre di debug.

## <a name="examine-thread-markers"></a>Esaminare i marcatori dei thread

1. Nel codice sorgente, individuare il `Console.WriteLine();` riga.

   1. Fare doppio clic nella **thread** finestra e selezionare **Mostra thread nell'origine** ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dal menu di scelta.

   Barra accanto al codice sorgente riga verrà ora visualizzato un *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "marcatore del Thread"). Il marcatore del thread indica l'interruzione di un thread in questa posizione. Se è presente più di un thread interrotto in corrispondenza della posizione, la ![più thread](../debugger/media/dbg-multithreaded-show-threads.png "più thread") icona viene visualizzata.

1. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati, che mostra il numero di ID thread e nome per il thread interrotto o thread. I nomi dei thread può essere `<No Name>`.

   >[!TIP]
   >Per identificare i thread senza nome, è possibile rinominarle nel **thread** finestra. Il thread e scegliere **Rinomina**.

1. Fare clic sul marcatore del thread nel codice sorgente per visualizzare le opzioni disponibili nel menu di scelta rapida.

## <a name="flag-and-unflag-threads"></a>Impostare e rimuovere i flag dei thread

È possibile contrassegnare i thread per tenere traccia dei thread che si desidera prestare particolare attenzione alla.

Impostare e rimuovere i flag dei thread da editor del codice sorgente o dal **thread** finestra. Scegliere se visualizzare solo con flag thread o tutti i thread, dal **posizione di Debug** oppure **thread** barre degli strumenti finestra. Le selezioni effettuate da qualsiasi posizione influiscono su tutte le posizioni.

### <a name="flag-and-unflag-threads-in-source-code"></a>Impostare e rimuovere i flag dei thread nel codice sorgente

1. Aprire il **posizione di Debug** sulla barra degli strumenti selezionando **View** > **barre degli strumenti** > **posizione di Debug**. È anche possibile fare doppio clic nell'area della barra degli strumenti e selezionare **posizione di Debug**.

1. Il **posizione di Debug** sulla barra degli strumenti dispone di tre campi: **processo**, **Thread**, e **Stack Frame**. Elenco a discesa la **Thread** elencare e sono il numero di thread. Nel **Thread** elenco, il thread attualmente in esecuzione è contrassegnato da un **>** simbolo.

1. Nella finestra del codice sorgente, passare il mouse su un'icona di marcatore del thread nella barra di navigazione e selezionare l'icona del contrassegno (o una delle icone flag vuoti) nel suggerimento dati. L'icona del contrassegno diventa rosso.

   È anche possibile fare doppio clic su un'icona di marcatore del thread, scegliere **Flag**e quindi selezionare un thread per contrassegnare il menu di scelta rapida.

1. Nel **posizione di Debug** sulla barra degli strumenti, seleziona il **Mostra solo thread con flag** icona ![Mostra thread con flag](../debugger/media/dbg-threads-show-flagged.png "Mostra thread con flag")al a destra il **Thread** campo. L'icona è disabilitata, a meno che uno o più thread sono contrassegnate.

   Solo i thread con flag sono ora inclusi i **Thread** elenco a discesa nella barra degli strumenti. Per visualizzare nuovamente tutti i thread, selezionare la **Mostra solo thread con flag** nuovamente clic sull'icona.

   >[!TIP]
   >Dopo che è stato applicato un contrassegno alcuni thread, è possibile posizionare il cursore nell'editor di codice, pulsante destro del mouse e selezionare **eseguire i thread con flag fino al cursore**. Assicurarsi di scegliere raggiungerà codice che tutti i thread con flag. **Eseguire i thread con flag fino al cursore** sospenderà thread nella riga di codice, rendendo più semplice controllare l'ordine di esecuzione da selezionata [blocco e sblocco dei thread](#bkmk_freeze).

1. Per attivare o disattivare lo stato con flag o rimozione del flag del thread attualmente in esecuzione, selezionare il flag single **attiva/disattiva lo stato contrassegnati del Thread corrente** pulsante della barra degli strumenti, a sinistra del **Mostra solo thread con flag** pulsante. Quando si contrassegna il thread corrente è utile per individuare il thread corrente quando vengono visualizzati solo i thread con flag.

1. Per rimuovere i flag un thread, passare il mouse sul marcatore del thread nel codice sorgente e selezionare l'icona di contrassegno rosso per cancellarla, o il marcatore del thread e scegliere **Rimuovi flag**.

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Impostare e rimuovere i flag dei thread nella finestra thread

Nel **thread** finestra thread con flag dispone red flag icone accanto agli durante il thread senza flag, se visualizzata, hanno icone vuote.

![Finestra thread](../debugger/media/dbg-threads-window.png "finestra thread")

Selezionare un'icona del flag di modifica dello stato di thread con flag o rimozione del flag, a seconda dello stato corrente.

È anche possibile fare doppio clic su una riga e selezionare **Flag**, **Rimuovi flag**, o **Rimuovi flag di tutti i thread** dal menu di scelta rapida.

Il **thread** sulla barra degli strumenti finestra ha anche una **Mostra solo con flag thread** pulsante, che è l'a destra una delle icone due flag. Lo stesso come il pulsante funziona sul **posizione di Debug** sulla barra degli strumenti e dei pulsanti determina la visualizzazione in entrambe le posizioni.

### <a name="other-threads-window-features"></a>Altre funzionalità di finestra thread

Nel **thread** finestra, selezionare l'intestazione di ogni colonna per ordinare i thread in base alla colonna. Selezionare di nuovo per invertire l'ordinamento. Se vengono visualizzati tutti i thread, selezionando la colonna di icona di contrassegno Ordina i thread in base allo stato con flag o rimozione del flag.

Nella seconda colonna della **thread** finestra (con nessuna intestazione) è la **Thread corrente** colonna. Una freccia gialla in questa colonna contrassegna il punto di esecuzione corrente.

Il **posizione** Mostra colonna in cui ogni thread viene visualizzato nel codice sorgente. Selezionare la freccia di espansione accanto al **posizione** voce o al passaggio del mouse sopra la voce, per visualizzare uno stack di chiamate parziale per il thread.

>[!TIP]
>Per visualizzare graficamente gli stack di chiamate per i thread, usare il [stack in parallelo](../debugger/using-the-parallel-stacks-window.md) finestra. Per aprire la finestra durante il debug, selezionare **Debug**> **Windows** > **stack in parallelo**.

Oltre a **Flag**, **Rimuovi flag**, e **Rimuovi flag di tutti i thread**, il menu di scelta rapida per **Thread** dispone di elementi della finestra:

- Il **Mostra thread nell'origine** pulsante.
- **Visualizzazione esadecimale**, quali modifiche il **ID Thread**s nel **thread** finestra da decimale in formato esadecimale.
- [Passare al Thread](#switch-to-another-thread), che attiva immediatamente l'esecuzione di tale thread.
- **Rinominare**, che consente di modificare il nome del thread.
- [Bloccare e sbloccare](#bkmk_freeze) comandi.

## <a name="bkmk_freeze"></a> Bloccare e sbloccare l'esecuzione di thread

Puoi bloccare e sbloccare, o sospendere e riprendere, i thread per controllare l'ordine in cui i thread di eseguono operazioni. Il blocco e sblocco dei thread possono aiutarti a risolvere i problemi di concorrenza, quali i deadlock e race condition.

> [!TIP]
> Per seguire un solo thread senza bloccare altri thread, che è anche uno scenario di debug comune, vedere [iniziare il debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Per bloccare e sbloccare i thread:**

1. Nel **thread** finestra, fare doppio clic su uno o più thread e quindi selezionare **Freeze**. Oggetto **pausa** icona nel **Thread corrente** colonna indica che il thread è bloccato.

1. Selezionare **colonne** nel **thread** degli strumenti della finestra e quindi selezionare **numero sospesi** per visualizzare il **numero sospesi** colonna. È il valore del conteggio sospeso per thread bloccato **1**.

1. Il thread bloccato di mouse e scegliere **Sblocca**.

   Il **pausa** icona scompare e il **numero sospesi** valore cambia in **0**.

## <a name="switch-to-another-thread"></a>Passare a un altro thread

È possibile visualizzare un **l'applicazione è in modalità di interruzione** finestra quando si prova a passare a un altro thread. In questa finestra indica che il thread non dispone di qualsiasi codice in grado di visualizzare il debugger corrente. Ad esempio, si potrebbe essere il debug di codice gestito, ma il thread è il codice nativo. La finestra contiene suggerimenti per la risoluzione del problema.

**Per passare a un altro thread:**

1. Nel **thread** finestra, prendere nota dell'ID del thread corrente, ovvero il thread con una freccia gialla nel **Thread corrente** colonna. È opportuno tornare a questo thread di continuare l'app.

1. Fare doppio clic su un altro thread e selezionare **Switch per Thread** dal menu di scelta rapida.

1. Osservare che è stato modificato il percorso di freccia gialla nel **thread** finestra. Il marcatore del thread corrente originale anche rimane, come una struttura.

   Esaminare la descrizione comando sul marcatore del thread nell'editor del codice sorgente e nell'elenco il **Thread** elenco a discesa nel **posizione di Debug** sulla barra degli strumenti. Osservare che il thread corrente è inoltre stato modificato non esiste.

1. Nel **posizione di Debug** sulla barra degli strumenti, selezionare un altro thread dalle **Thread** elenco. Si noti che il thread corrente cambia anche in altri due posizioni.

1. Nell'editor del codice sorgente, fare doppio clic su un marcatore del thread, scegliere **Switch per Thread**e selezionare un altro thread dall'elenco. Osservare che il thread corrente cambia in tutti i tre posizioni.

Con il marcatore del thread nel codice sorgente, è possibile passare solo ai thread che sono stati interrotti in quella posizione. Con la finestra **Thread** e la barra degli strumenti **Posizione di debug** è possibile passare a tutti i tipi di thread.

A questo punto, dopo aver appreso le nozioni fondamentali di debug di applicazioni a thread multipli. È possibile osservare, flag e rimuovere i flag e bloccare e sbloccare i thread con il **thread** finestra, il **Thread** nell'elenco il **posizione di Debug** sulla barra degli strumenti o i marcatori dei thread nel editor di codice sorgente.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
