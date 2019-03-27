---
title: Informazioni su come eseguire il debug di applicazioni multithreading
description: Eseguire il debug usando le finestre Espressioni di controllo parallelo e stack in parallelo in Visual Studio
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6d72edaf889aaf682f40a36278ea1fdf05ff989
ms.sourcegitcommit: 8d453b345c72339c37b489a140dad00b244e6ba4
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/26/2019
ms.locfileid: "58475994"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Iniziare il debug di applicazioni multithreading (C#, Visual Basic, C++)

Visual Studio offre diversi strumenti e gli elementi dell'interfaccia utente per il debug di applicazioni multithreading. Questa esercitazione illustra come usare i marcatori dei thread, il **stack in parallelo** finestra, il **espressioni di controllo parallela** finestra punti di interruzione condizionali e i punti di interruzione di filtro. Il completamento di questa esercitazione consentirà di familiarizzare con le funzionalità di Visual Studio per il debug di applicazioni multithreading.

Questi due argomenti forniscono informazioni aggiuntive sull'uso di altri strumenti di debug con multithreading:

- Usare la **posizione di Debug** sulla barra degli strumenti e il **thread** finestra, vedere [procedura dettagliata: eseguire il Debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

- Per un esempio che usa <xref:System.Threading.Tasks.Task> (codice gestito) e il runtime di concorrenza (C++), vedere [procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md). Per suggerimenti di debug generali applicabili a tipi di applicazioni più a thread multipli, leggere tale argomento sia presente uno.

È necessario innanzitutto un progetto di applicazione a thread multipli. Vedere l'esempio seguente:

## <a name="create-a-multithreaded-app-project"></a>Creare un progetto di app a thread multipli

1. Aprire Visual Studio e creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Tipo di **Ctrl + Q** per aprire la casella di ricerca, digitare **console** (o **c + +**), scegliere **modelli**e quindi:
    
    - Per C# o Visual Basic, scegli **Crea nuovo progetto App Console (.NET Framework)** entrambi C# o Visual Basic. Nella finestra di dialogo visualizzata, scegliere **Create**.
    - Per C++, scegliere **Crea nuovo progetto App Console** per C++. Nella finestra di dialogo visualizzata, scegliere **Create**.

    Quindi, digitare un nome simile **MyThreadWalkthroughApp** e fare clic su **crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra di **nuovo progetto** dialogo finestra, scegliere le opzioni seguenti:

    - Per un C# app, sotto **Visual C#** , scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App Console (.NET Framework)**.
    - Per un'app Visual Basic, sotto **Visual Basic**, scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App Console (.NET Framework)**.
    - Per un'app C++, sotto **Visual C++**, scegliere **Windows Desktop**, quindi scegliere **applicazione Console Windows**.

    Quindi, digitare un nome simile **MyThreadWalkthroughApp** e fare clic su **OK**.
    ::: moniker-end

    Se non viene visualizzato il **App Console** modello di progetto, passa alla **Tools** > **Ottieni strumenti e funzionalità...** , che viene aperto il programma di installazione Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET** o **Sviluppo di applicazioni desktop con C++**, quindi scegliere **Modifica**.

1. Scegliere **OK**.

    Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il file di origine potrebbe essere chiamato *Program.cs*, *MyThreadWalkthroughApp. cpp*, o *Module1.vb*.

1. Eliminare il codice riportato nel file di origine e sostituirlo con il codice di esempio appropriato riportato di seguito.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "pch.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. Scegliere **Salva tutto** dal menu **File**.

1. (Solo Visual Basic) In Esplora soluzioni (riquadro a destra), fare clic sul nodo del progetto, scegliere **proprietà**. Sotto il **Application** scheda, modificare il **oggetto di avvio** a **semplice**.

## <a name="debug-the-multithreaded-app"></a>Il debug dell'app a thread multipli

1. Nell'editor del codice sorgente, cercare uno dei frammenti di codice seguenti:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Fare clic sul margine a sinistra del `Thread.Sleep` o `std::this_thread::sleep_for` istruzione per inserire un nuovo punto di interruzione.

    Nella barra di navigazione, un cerchio rosso indica che un punto di interruzione è impostato in questa posizione.

2. Nel **Debug** dal menu **Avvia debug** (**F5**).

    Visual Studio compila la soluzione, l'app viene avviata l'esecuzione con il debugger collegato e quindi l'app si arresta nel punto di interruzione.

3. Nell'editor del codice sorgente, individuare la riga che contiene il punto di interruzione.

### <a name="ShowThreadsInSource"></a>Individuare il marcatore del thread  

1.  Nella barra degli strumenti di Debug, selezionare la **Mostra thread nell'origine** pulsante ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Premere **F11** una volta per far avanzare la riga di un debugger del codice.

3.  All'estrema sinistra della finestra, In questa riga, si noterà una *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") che è simile a due thread doppini intrecciati. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Un marcatore del thread potrebbe essere parzialmente nascosta da un punto di interruzione.

4.  Posizionare il puntatore del mouse sul marcatore del thread. Un suggerimento dati verrà visualizzato il numero di ID thread e nome di ciascun thread interrotto. In questo caso, il nome è probabilmente `<noname>`.

5.  Selezionare il marcatore del thread per visualizzare le opzioni disponibili nel menu di scelta rapida.

### <a name="ParallelStacks"></a>Visualizzare le sedi di thread

Nel **stack in parallelo** finestra, è possibile passare tra una visualizzazione thread e (per la programmazione basata su attività) Visualizza le attività e si possono visualizzare informazioni sullo stack di chiamate per ogni thread. In questa app, è possibile usare la visualizzazione dei thread.

1. Aprire il **stack in parallelo** finestra scegliendo **Debug** > **Windows** > **stack in parallelo**. Dovrebbe essere simile al seguente. Le informazioni esatte variano a seconda della posizione corrente di ogni thread, l'hardware e il linguaggio di programmazione.

    ![Finestra Stack in parallelo](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In questo esempio, da sinistra a destra viene visualizzato queste informazioni per il codice gestito:

    - Il thread principale (lato sinistro) è stato arrestato sul `Thread.Start`, in cui il punto di interruzione è indicato dall'icona marcatore thread ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Due thread di avere immesso il `ServerClass.InstanceMethod`, uno dei quali è il thread corrente (freccia gialla), mentre l'altro thread è stato arrestato `Thread.Sleep`.
    - Un nuovo thread (sulla destra) sta avviando anche ma è stato arrestato sul `ThreadHelper.ThreadStart`.

2.  Mouse nel **stack in parallelo** finestra per visualizzare le opzioni disponibili nel menu di scelta rapida.

    È possibile eseguire varie azioni da questi menu di scelta rapida, ma per questa esercitazione verrà illustrato più di questi dettagli nel **espressioni di controllo parallela** finestra (sezioni).

    > [!NOTE]
    > Per visualizzare un elenco con informazioni su ogni thread, usare il **thread** finestra invece. Visualizzare [procedura dettagliata: Debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Impostare un'espressione di controllo in una variabile

1. Aprire il **espressioni di controllo parallela** finestra selezionando **Debug** > **Windows** > **espressioni di controllo parallela**  >  **Espressioni di controllo 1 in parallelo**.

2. Selezionare la cella in cui vengono visualizzate le `<Add Watch>` testo (o la cella di intestazione vuota nella colonna 4 °) e immettere `data`.

    Nella finestra vengono visualizzati i valori per la variabile di dati per ogni thread.

3. Selezionare la cella in cui vengono visualizzate le `<Add Watch>` testo (o la cella di intestazione vuota nella colonna 5) e immettere `count`.

    I valori per il `count` variabile per ogni thread vengono visualizzati nella finestra. Se non viene visualizzato ancora così tante informazioni, provare a premendo **F11** alcune volte per anticipare l'esecuzione dei thread nel debugger.

    ![Finestra Espressioni di controllo in parallelo](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Fare clic su una delle righe della finestra per visualizzare le opzioni disponibili.

### <a name="flag-and-unflag-threads"></a>Impostare e rimuovere i flag dei thread
È possibile contrassegnare i thread per tenere traccia dei thread importanti e ignorare gli altri thread.

1. Nel **espressioni di controllo parallela** finestra, tenendo premuto il tasto le **MAIUSC** , selezionare più righe.

2. Fare doppio clic e selezionare **Flag**.

    Tutti i thread selezionati vengono contrassegnati. A questo punto, è possibile filtrare per mostrare solo thread con flag.

3.  Nel **espressioni di controllo parallela** finestra, seleziona la **Mostra solo thread con flag** pulsante ![Mostra thread con flag](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Solo i thread con flag visualizzato nell'elenco.

    > [!TIP]
    > Dopo che è stato applicato un contrassegno alcuni thread, è possibile fare doppio clic su una riga di codice nell'editor del codice e scegliere **eseguire i thread con flag fino al cursore**. Assicurarsi di scegliere raggiungerà codice che tutti i thread con flag. Visual Studio verrà messo in pausa thread nella riga selezionata di codice, rendendo più semplice controllare l'ordine di esecuzione da [blocco e sblocco dei thread](#bkmk_freeze).

4.  Selezionare il **Mostra solo thread con flag** pulsante nuovo per passare di nuovo alla **Mostra tutti i thread** modalità.

5. Per rimuovere i flag dei thread, fare doppio clic su uno o più thread con flag nel **espressioni di controllo parallela** finestra e selezionare **Rimuovi flag**.

### <a name="bkmk_freeze"></a> Bloccare e sbloccare l'esecuzione di thread

> [!TIP]
> È possibile bloccare e sbloccare (sospendere e riprendere) i thread per controllare l'ordine in cui i thread di eseguono operazioni. Ciò consente di risolvere i problemi di concorrenza, ad esempio i deadlock e race condition.

1.  Nel **espressioni di controllo parallela** finestra, con tutte le righe selezionate, pulsante destro del mouse e selezionare **Freeze**.

    Nella seconda colonna, viene visualizzata un'icona di sospensione per ogni riga. L'icona di sospensione indica che il thread è bloccato.

2.  Deselezionare tutte le altre righe selezionando una sola riga.

3.  Fare doppio clic su una riga e selezionare **Sblocca**.

    L'icona di sospensione viene chiuso in questa riga, che indica che il thread non è più bloccato.

4.  Passare all'editor di codice e premere **F11**. Viene eseguito solo il thread non bloccato.

    L'app può anche creare un'istanza di alcuni nuovi thread. Tutti i nuovi thread sono flag e non sono bloccati.

### <a name="bkmk_follow_a_thread"></a> Seguire un solo thread con punti di interruzione condizionali

Può essere utile seguire l'esecuzione di un singolo thread nel debugger. Un modo per eseguire questa operazione è bloccando i thread che non si sono interessati. In alcuni scenari potrebbe essere necessario seguire un solo thread senza bloccare altri thread, ad esempio per riprodurre un bug specifico. Per eseguire un thread senza bloccare altri thread, è necessario evitare l'interruzione del codice, ad eccezione nel thread in cui si è interessati. È possibile farlo impostando un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

È possibile impostare i punti di interruzione in condizioni diverse, ad esempio il nome del thread o l'ID del thread. Potrebbe essere utile consiste nell'impostare la condizione su dati che è univoco per ogni thread. Si tratta di uno scenario di debug comune, in cui è più interessati a un valore di dati specifico rispetto in qualsiasi thread specifico.

1. Il pulsante destro del punto di interruzione creato in precedenza e selezionare **condizioni**.

2. Nel **impostazioni punto di interruzione** finestra immettere `data == 5` per l'espressione condizionale.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Se è più interessati a un thread specifico, usare un nome del thread o un ID di thread per la condizione. Per eseguire questa operazione **impostazioni punto di interruzione** finestra, seleziona **filtro** anziché **espressione condizionale**e seguire i suggerimenti di filtro. È possibile denominare i thread nel codice dell'app, man mano che gli ID thread cambiano quando si riavvia il debugger.

3. Chiudi il **impostazioni punto di interruzione** finestra.

4. Selezionare il riavvio ![App riavviare](../debugger/media/dbg-tour-restart.png "RestartApp") per riavviare la sessione di debug.

    Esecuzione verrà interrotta nel codice sul thread in cui valore della variabile di dati è 5. Nel **espressioni di controllo parallela** finestra, cercare la freccia gialla che indica il contesto di debug corrente.

5. A questo punto, è possibile saltare il codice (**F10**) e istruzioni nel codice (**F11**) e seguire l'esecuzione del thread singolo.

    Purché la condizione di punto di interruzione è univoca per il thread e il debugger non raggiungere qualsiasi altro punto di interruzione in altri thread (potrebbe essere necessario disabilitare le), è possibile saltare il codice e l'istruzione nel codice senza dover passare agli altri thread.

    > [!NOTE]
    > Quando si arriva il debugger, verranno eseguiti tutti i thread. Tuttavia, il debugger non interrompe nel codice in altri thread, a meno che uno degli altri thread raggiunge un punto di interruzione.

## <a name="see-also"></a>Vedere anche

- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Procedura: usare la finestra Stack paralleli](../debugger/using-the-parallel-stacks-window.md)
- [Procedura: Usare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)