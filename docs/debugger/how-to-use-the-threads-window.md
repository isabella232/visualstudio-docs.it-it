---
title: Eseguire il debug di un'app multithreading
description: Eseguire il debug usando la finestra Thread e la barra degli strumenti Posizione di debug in Visual Studio
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 86dd3c980781cb0dd3d91f9d50cd3464d95c0d61
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709911"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Procedura dettagliata: Eseguire il debug di un'app multithreading usando la finestra Thread (C#, Visual Basic, C++)

Diversi Visual Studio dell'interfaccia utente consentono di eseguire il debug di app multithreading. Questo articolo presenta le funzionalità di debug multithreading nella finestra dell'editor del **codice,** nella barra degli strumenti Posizione di debug e **nella finestra** Thread. Per informazioni su altri strumenti per il debug di app multithreading, vedere [Introduzione al debug di app multithreading.](../debugger/get-started-debugging-multithreaded-apps.md)

Il completamento di questa esercitazione richiede solo pochi minuti e consente di acquisire familiarità con le nozioni di base del debug di app multithreading.

## <a name="create-a-multithreaded-app-project"></a>Creare un progetto di app multithreading

Creare il progetto di app multithreading seguente da usare in questa esercitazione:

1. Aprire Visual Studio e creare un nuovo progetto.

   ::: moniker range=">=vs-2019"

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

   Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#** o **C++ dall'elenco** Linguaggio e quindi scegliere Windows **dall'elenco** Piattaforma . 

   Dopo aver applicato i filtri del linguaggio e della piattaforma, scegliere **App console** per .NET Core o per C++, quindi scegliere **Avanti.**

   > [!NOTE]
   > Se non viene visualizzato il modello corretto, passare **a** Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro Sviluppo **multipiattaforma .NET Core** o Sviluppo di applicazioni desktop con **C++,** quindi **scegliere Modifica.**

   Nella finestra **Configura il nuovo progetto** digitare o immettere *MyThreadWalkthroughApp* nella casella **Project nome.** Scegliere quindi **Avanti o** **Crea,** a seconda dell'opzione disponibile.

   Per .NET Core, scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**

   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro sinistro della finestra **di dialogo Nuovo** progetto scegliere le opzioni seguenti:

   - Per un'app C#, in **Visual C#** scegliere **Windows Desktop** e quindi nel riquadro centrale scegliere App console **(.NET Framework).**
   - Per un'app C++, in **Visual C++** scegliere **Windows Desktop** e quindi scegliere Windows **Applicazione console**.

   Se non viene visualizzata l'app **console (.NET Framework)** o, per C++, il modello di progetto **App** console, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro Sviluppo **per desktop .NET** o Sviluppo di applicazioni **desktop con C++,** quindi **scegliere Modifica.**

   Digitare quindi un nome come *MyThreadWalkthroughApp e* fare clic su **OK.**

   Selezionare **OK**.
   ::: moniker-end

   Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il file di origine potrebbe essere denominato *Program.cs*, *MyThreadWalkthroughApp.cpp* o *Module1.vb*.

1. Sostituire il codice nel file di origine con il codice di esempio C# o C++ di [Introduzione al debug di app multithreading](../debugger/get-started-debugging-multithreaded-apps.md).

1. Selezionare **File**  >  **Salva tutto.**

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

1. Impostare un punto di interruzione sulla riga facendo clic sulla barra di spostamento a sinistra oppure selezionando `Console.WriteLine();` la riga e premendo **F9.**

   Il punto di interruzione viene visualizzato come cerchio rosso nella barra di spostamento sinistra accanto alla riga di codice.

1. Selezionare **Debug**  >  **Avvia debug** o premere **F5.**

   L'app viene avviata in modalità di debug e viene sospesa in corrispondenza del punto di interruzione.

1. In modalità di interruzione aprire la **finestra Thread** selezionando **Debug** Windows  >    >  **Thread**. È necessario essere in una sessione di debug per aprire o visualizzare i **thread e** altre finestre di debug.

## <a name="examine-thread-markers"></a>Esaminare i marcatori di thread

1. Nel codice sorgente individuare la `Console.WriteLine();` riga .

   1. Fare clic con il pulsante destro **del mouse nella** finestra Thread e scegliere Mostra thread **nell'origine** Mostra ![thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") dal menu.

   La barra di margine accanto alla riga del codice sorgente ora visualizza l'icona del *marcatore* thread ![Marcatore thread](../debugger/media/dbg-thread-marker.png "Marcatore del thread"). Il marcatore del thread indica l'interruzione di un thread in questa posizione. Se nel percorso sono presenti più thread arrestati, viene visualizzata ![l'icona di più](../debugger/media/dbg-multithreaded-show-threads.png "thread multipli") thread.

1. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati che mostra il nome e il numero ID thread per il thread o i thread arrestati. I nomi dei thread possono essere `<No Name>` .

   >[!TIP]
   >Per identificare più facilmente i thread senza nome, è possibile rinominarli nella **finestra** Thread. Fare clic con il pulsante destro del mouse sul thread e **scegliere Rinomina.**

1. Fare clic con il pulsante destro del mouse sul marcatore del thread nel codice sorgente per visualizzare le opzioni disponibili nel menu di scelta rapida.

## <a name="flag-and-unflag-threads"></a>Impostare e rimuovere i flag dei thread

È possibile contrassegnare i thread per tenere traccia dei thread a cui si vuole prestare particolare attenzione.

Contrassegnare e rimuovere i flag dei thread dall'editor del codice sorgente o dalla **finestra** Thread. Scegliere se visualizzare solo i thread contrassegnati o tutti i thread dalle barre degli strumenti della finestra Posizione **di** **debug** o Thread. Le selezioni effettuate da qualsiasi posizione influiscono su tutte le posizioni.

### <a name="flag-and-unflag-threads-in-source-code"></a>Contrassegnare e rimuovere i flag dei thread nel codice sorgente

1. Aprire la barra **degli strumenti Posizione di** debug selezionando Visualizza **barre** degli strumenti  >  **Posizione** di  >  **debug**. È anche possibile fare clic con il pulsante destro del mouse nell'area della barra degli strumenti e **scegliere Posizione di debug.**

1. La **barra degli strumenti Posizione** di debug include tre **campi: Processo**, **Thread** e Stack **Frame**. Nell'elenco **a discesa Thread** e notare il numero di thread presenti. **Nell'elenco Thread** il thread attualmente in esecuzione è contrassegnato da un **>** simbolo.

1. Nella finestra del codice sorgente passare il puntatore del mouse sull'icona di un marcatore di thread nella barra e selezionare l'icona del flag (o una delle icone di flag vuote) nel suggerimento dati. L'icona del flag diventa rossa.

   È anche possibile fare clic con il pulsante destro del mouse sull'icona di un marcatore di thread, scegliere **Contrassegna** e quindi selezionare un thread da contrassegnare dal menu di scelta rapida.

1. Sulla barra **degli strumenti**  Posizione di debug selezionare l'icona Mostra solo thread contrassegnati ![a](../debugger/media/dbg-threads-show-flagged.png "Mostra thread contrassegnati")destra del **campo Thread.** L'icona è disattivata a meno che uno o più thread non siano contrassegnati.

   Solo il thread contrassegnato viene ora visualizzato **nell'elenco a discesa Thread** sulla barra degli strumenti. Per visualizzare nuovamente tutti i thread, selezionare di **nuovo l'icona Mostra** solo thread contrassegnati .

   >[!TIP]
   >Dopo aver contrassegnato alcuni thread, è possibile posizionare il cursore nell'editor del codice, fare clic con il pulsante destro del mouse e scegliere Esegui thread **contrassegnati fino al cursore.** Assicurarsi di scegliere il codice che tutti i thread contrassegnati raggiungeranno. **Esegui thread contrassegnati fino** al cursore sospende i thread nella riga di codice selezionata, semplificando il controllo dell'ordine di esecuzione bloccando e scondendo [i thread](#bkmk_freeze).

1. Per attivare o disattivare lo stato contrassegnato o non contrassegnato  del thread attualmente in esecuzione, selezionare  il pulsante della barra degli strumenti Attiva/Disattiva stato contrassegnato thread corrente a sinistra del pulsante Mostra solo thread contrassegnati. L'applicazione di flag al thread corrente è utile per individuare il thread corrente quando vengono visualizzati solo i thread contrassegnati.

1. Per rimuovere il flag di un thread, passare il puntatore del mouse sul marcatore del thread nel codice sorgente e selezionare l'icona del flag rosso per cancellarlo oppure fare clic con il pulsante destro del mouse sul marcatore del thread e scegliere Annulla flag **.**

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Contrassegnare e rimuovere i flag dei thread nella finestra Thread

Nella finestra **Thread,** accanto ai thread contrassegnati sono presenti icone con flag rosso, mentre i thread senza flag, se visualizzati, hanno icone vuote.

![Finestra Thread](../debugger/media/dbg-threads-window.png "Finestra Thread")

Selezionare un'icona flag per impostare lo stato del thread su contrassegnato o non contrassegnato, a seconda dello stato corrente.

È anche possibile fare clic con il pulsante destro del mouse su una riga e scegliere **Contrassegna** **,** Annulla flago Annulla flag per tutti i thread **dal** menu di scelta rapida.

La **barra degli** strumenti  della finestra Thread include anche un pulsante Mostra solo thread contrassegnati, che è l'icona a destra di una delle due icone dei flag. Funziona come il pulsante sulla barra degli strumenti Posizione di **debug** e entrambi i pulsanti controllano la visualizzazione in entrambe le posizioni.

### <a name="other-threads-window-features"></a>Altre funzionalità della finestra Thread

Nella finestra **Thread selezionare** l'intestazione di qualsiasi colonna per ordinare i thread in base a tale colonna. Selezionare di nuovo per invertire l'ordinamento. Se vengono visualizzati tutti i thread, selezionando la colonna icona flag i thread vengono ordinati in base allo stato contrassegnato o non contrassegnato.

La seconda colonna della **finestra Thread** (senza intestazione) è la **colonna Thread** corrente. Una freccia gialla in questa colonna contrassegna il punto di esecuzione corrente.

La **colonna Posizione** mostra dove viene visualizzato ogni thread nel codice sorgente. Selezionare la freccia di espansione accanto alla **voce Posizione** oppure passare il mouse sulla voce per visualizzare uno stack di chiamate parziale per il thread.

>[!TIP]
>Per una visualizzazione grafica degli stack di chiamate per i thread, usare la [finestra Stack in](../debugger/using-the-parallel-stacks-window.md) parallelo. Per aprire la finestra durante il debug, selezionare >  **Debug Windows** Stack  >  **paralleli**.

Oltre a **Flag**, **Unflag e Unflag** **All Threads**, il menu di scelta rapida per gli elementi della finestra **Thread** include:

- Pulsante **Mostra thread nell'origine.**
- **Visualizzazione esadecimale,** che modifica gli **ID** thread nella finestra **Thread** dal formato decimale al formato esadecimale.
- [Passare a thread](#switch-to-another-thread), che passa immediatamente all'esecuzione a tale thread.
- **Rinominare**, che consente di modificare il nome del thread.
- [Comandi Freeze e Thaw.](#bkmk_freeze)

## <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Bloccare e scoscire l'esecuzione del thread

È possibile bloccare e scoscire, o sospendere e riprendere, i thread per controllare l'ordine in cui i thread eseguono il lavoro. Il blocco e lo scosto dei thread consentono di risolvere i problemi di concorrenza, ad esempio deadlock e race conditions.

> [!TIP]
> Per seguire un singolo thread senza bloccare altri thread, che è anche uno scenario di debug comune, vedere Introduzione al [debug di applicazioni multithreading](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).

**Per bloccare e sbloccare i thread:**

1. Nella finestra **Thread** fare clic con il pulsante destro del mouse su qualsiasi thread e quindi scegliere **Blocca**. **Un'icona** Sospendi nella **colonna Thread** corrente indica che il thread è bloccato.

1. Selezionare **Colonne** nella barra **degli strumenti della** finestra Thread e quindi Selezionare **Conteggio sospeso** per visualizzare la colonna **Conteggio sospeso.** Il valore del conteggio sospeso per il thread bloccato è **1.**

1. Fare clic con il pulsante destro del mouse sul thread bloccato e **scegliere Thaw**.

   **L'icona** Pause (Sospendi) scompare e **il valore suspended count (Conteggio** sospeso) viene impostato su **0.**

## <a name="switch-to-another-thread"></a>Passare a un altro thread

Quando si tenta di passare a un altro thread, è possibile che l'applicazione sia **in** modalità di interruzione. Questa finestra indica che il thread non dispone di codice che il debugger corrente può visualizzare. Ad esempio, è possibile eseguire il debug di codice gestito, ma il thread è codice nativo. La finestra offre suggerimenti per la risoluzione del problema.

**Per passare a un altro thread:**

1. Nella finestra **Thread** prendere nota dell'ID thread corrente, ovvero il thread con una freccia gialla nella **colonna Thread** corrente. È necessario tornare a questo thread per continuare l'app.

1. Fare clic con il pulsante destro del mouse su un thread diverso e **scegliere Passa** a thread dal menu di scelta rapida.

1. Si noti che la posizione della freccia gialla è stata modificata nella **finestra** Thread. Anche il marcatore thread corrente originale rimane, come contorno.

   Esaminare la descrizione comando sul marcatore di thread nell'editor del codice sorgente e l'elenco nell'elenco **a** discesa Thread sulla barra **degli strumenti Percorso di** debug. Si noti che anche il thread corrente è stato modificato.

1. Sulla barra **degli strumenti Percorso di** debug selezionare un thread diverso dall'elenco **Thread** . Si noti che il thread corrente cambia anche nelle altre due posizioni.

1. Nell'editor del codice sorgente fare clic con il pulsante destro del mouse su un marcatore di thread, scegliere Passa a **thread** e selezionare un altro thread dall'elenco. Si noti che il thread corrente cambia in tutte e tre le posizioni.

Con il marcatore di thread nel codice sorgente, è possibile passare solo ai thread arrestati in tale posizione. Con la finestra **Thread** e la barra degli strumenti **Posizione di debug** è possibile passare a tutti i tipi di thread.

A questo punto sono stati appresi i concetti di base del debug di app multithreading. È possibile osservare, contrassegnare e rimuovere il flag e  bloccare e sbloccare  i thread usando la finestra Thread, l'elenco **Thread** nella barra degli strumenti Percorso di debug o i marcatori di thread nell'editor del codice sorgente.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
