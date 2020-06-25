---
title: Informazioni su come eseguire il debug di applicazioni multithreading
description: Eseguire il debug usando le finestre Stack in parallelo e espressioni di controllo in parallelo in Visual Studio
ms.custom: ''
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30fd29357ab8b42ea6a8baa6412f9ccf7eafed28
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350511"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Introduzione al debug di applicazioni multithread (C#, Visual Basic, C++)

Visual Studio offre diversi strumenti ed elementi dell'interfaccia utente che consentono di eseguire il debug di applicazioni multithread. Questa esercitazione illustra come usare i marcatori di thread, la finestra **stack in parallelo** , la finestra espressioni di **controllo in parallelo** , i punti di interruzione condizionali e i punti di interruzione dei filtri. Il completamento di questa esercitazione consentirà di acquisire familiarità con le funzionalità di Visual Studio per il debug di applicazioni multithread.

Questi due argomenti forniscono informazioni aggiuntive sull'uso di altri strumenti di debug multithreading:

- Per usare la barra degli strumenti **posizione di debug** e la finestra **thread** , vedere [procedura dettagliata: eseguire il debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

- Per un esempio che usa <xref:System.Threading.Tasks.Task> (codice gestito) e il runtime di concorrenza (C++), vedere [procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md). Per suggerimenti generali per il debug che si applicano alla maggior parte dei tipi di applicazioni multithread, leggere l'argomento e questo argomento.

Per prima cosa è necessario un progetto di applicazione multithreading. Di seguito è riportato un esempio.

## <a name="create-a-multithreaded-app-project"></a>Creare un progetto di app multithread

1. Aprire Visual Studio e creare un nuovo progetto.

   ::: moniker range=">=vs-2019"

   Se la finestra di avvio non è aperta, **File** scegliere > **finestra di avvio**file.

   Nella finestra Start scegliere **Crea un nuovo progetto**.

   Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Successivamente, scegliere **C#**, **C++** o **Visual Basic** dall'elenco lingua, quindi scegliere **Windows** dall'elenco piattaforma. 

   Dopo aver applicato la lingua e i filtri della piattaforma, scegliere l' **app console (.NET Core)** o, per C++, modello **applicazione console** , quindi scegliere **Avanti**.

   > [!NOTE]
   > Se non viene visualizzato il modello corretto, passare a **strumenti**  >  **Ottieni strumenti e funzionalità...**, che consente di aprire la programma di installazione di Visual Studio. Scegliere il carico di lavoro sviluppo per **desktop .NET** o **sviluppo desktop con C++** , quindi scegliere **modifica**.

   Nella finestra **Configura nuovo progetto** Digitare o immettere *MyThreadWalkthroughApp* nella casella **nome progetto** . Quindi scegliere **Crea**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Dalla barra dei menu in alto scegliere **file**  >  **nuovo**  >  **progetto**. Nel riquadro sinistro della finestra di dialogo **nuovo progetto** scegliere le opzioni seguenti:

   - Per un'app C#, in **Visual c#** scegliere **desktop di Windows**e quindi nel riquadro centrale scegliere **app console (.NET Framework)**.
   - Per un'app Visual Basic, in **Visual Basic**scegliere **desktop di Windows**e quindi nel riquadro centrale scegliere **app console (.NET Framework)**.
   - Per un'app C++, in **Visual C++** scegliere **desktop di Windows**, quindi scegliere **applicazione console di Windows**.

   Se non viene visualizzata l' **app console (.NET Core)** o, per C++, il modello di progetto di **app console** , passare a **strumenti**  >  **Ottieni strumenti e funzionalità...**, che consente di aprire la programma di installazione di Visual Studio. Scegliere il carico di lavoro sviluppo per **desktop .NET** o **sviluppo desktop con C++** , quindi scegliere **modifica**.

   Digitare quindi un nome come *MyThreadWalkthroughApp* e fare clic su **OK**.

   Fare clic su **OK**.
   ::: moniker-end

   Verrà visualizzato un nuovo progetto console. Una volta creato il progetto, viene visualizzato un file di origine. A seconda della lingua scelta, il file di origine potrebbe essere denominato *Program.cs*, *MyThreadWalkthroughApp. cpp*o *Module1. vb*.

1. Eliminare il codice visualizzato nel file di origine e sostituirlo con l'elenco di codici di esempio appropriato riportato di seguito.

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
                "The instance method called by the worker thread has ended. " + data);
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
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
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
                    "The instance method called by the worker thread has ended. " + data)
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

1. (Solo Visual Basic) In Esplora soluzioni (riquadro a destra), fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**. Nella scheda **applicazione** impostare l'oggetto di **avvio** su **semplice**.

## <a name="debug-the-multithreaded-app"></a>Eseguire il debug dell'app multithread

1. Nell'editor del codice sorgente cercare uno dei frammenti di codice seguenti:

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

1. Fare clic con il pulsante destro del mouse nella barra di navigazione a sinistra dell' `Thread.Sleep` `std::this_thread::sleep_for` istruzione o per inserire un nuovo punto di interruzione.

    Nella barra di navigazione un cerchio rosso indica che è stato impostato un punto di interruzione in questa posizione.

2. Scegliere **Avvia debug** (**F5**) dal menu **debug** .

    Visual Studio compila la soluzione, l'app viene avviata con il debugger collegato, quindi l'app viene arrestata in corrispondenza del punto di interruzione.

3. Nell'editor del codice sorgente individuare la riga che contiene il punto di interruzione.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>Individuare il marcatore del thread  

1. Nella barra degli strumenti Debug selezionare il pulsante **Mostra thread nel codice sorgente** ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Premere **F11** una volta per far avanzare al debugger una riga di codice.

3. All'estrema sinistra della finestra, In questa riga verrà visualizzato un ![marcatore del thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") dell'icona del *marcatore del thread* simile a due thread con torsione. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Un marcatore di thread può essere parzialmente nascosto da un punto di interruzione.

4. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un DataTip che indica il nome e il numero ID del thread per ogni thread arrestato. In questo caso, il nome è probabilmente `<noname>` .

5. Selezionare il marcatore del thread per visualizzare le opzioni disponibili nel menu di scelta rapida.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>Visualizzare i percorsi dei thread

Nella finestra **stack in parallelo** è possibile passare da una visualizzazione thread alla visualizzazione attività (per la programmazione basata su attività) e visualizzare le informazioni sullo stack di chiamate per ogni thread. In questa app è possibile usare la visualizzazione thread.

1. Aprire la finestra **stack in parallelo** scegliendo **debug**  >  stack in parallelo di**Windows**  >  **Parallel Stacks**. Verrà visualizzata una schermata simile alla seguente. Le informazioni esatte variano a seconda della posizione corrente di ogni thread, dell'hardware e del linguaggio di programmazione.

    ![Finestra stack in parallelo](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In questo esempio, da sinistra a destra vengono visualizzate queste informazioni per il codice gestito:

    - Il thread principale (lato sinistro) è stato arrestato in `Thread.Start` , dove il punto di arresto è indicato dal ![marcatore del thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")dell'icona del marcatore del thread.
    - Due thread hanno immesso `ServerClass.InstanceMethod` , uno dei quali è il thread corrente (freccia gialla), mentre l'altro thread è stato arrestato in `Thread.Sleep` .
    - Viene avviato anche un nuovo thread (a destra), ma viene arrestato in `ThreadHelper.ThreadStart` .

2. Fare clic con il pulsante destro del mouse su voci nella finestra **stack in parallelo** per visualizzare le opzioni disponibili nel menu di scelta rapida.

    È possibile eseguire diverse azioni da questi menu con il pulsante destro del mouse, ma per questa esercitazione verranno illustrati i dettagli nella finestra espressione di **controllo in parallelo** (sezioni successive).

    > [!NOTE]
    > Per visualizzare una visualizzazione elenco con le informazioni su ogni thread, usare invece la finestra **thread** . Vedere [procedura dettagliata: eseguire il debug di un'applicazione multithread](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Impostare un'espressione di controllo su una variabile

1. Aprire la finestra **espressioni di controllo in parallelo** selezionando **debug**  >  **Windows**  >  **Parallel**Watch  >  **Parallel Watch 1**.

2. Selezionare la cella in cui viene visualizzato il `<Add Watch>` testo (o la cella di intestazione vuota nella quarta colonna) e immettere `data` .

    I valori per la variabile di dati per ogni thread vengono visualizzati nella finestra.

3. Selezionare la cella in cui viene visualizzato il `<Add Watch>` testo (o la cella di intestazione vuota nella quinta colonna) e immettere `count` .

    I valori per la `count` variabile per ogni thread vengono visualizzati nella finestra. Se questa quantità di informazioni non è ancora visualizzata, provare a premere **F11** alcune volte per avanzare l'esecuzione dei thread nel debugger.

    ![Finestra espressioni di controllo in parallelo](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Fare clic con il pulsante destro del mouse su una delle righe della finestra per visualizzare le opzioni disponibili.

### <a name="flag-and-unflag-threads"></a>Impostare e rimuovere i flag dei thread
È possibile contrassegnare i thread per tenere traccia dei thread importanti e ignorare gli altri thread.

1. Nella finestra espressione di **controllo in parallelo** tenere premuto il tasto **MAIUSC** e selezionare più righe.

2. Fare clic con il pulsante destro del mouse e selezionare **flag**.

    Tutti i thread selezionati sono contrassegnati. A questo punto, è possibile filtrare per visualizzare solo i thread con flag.

3. Nella finestra espressione di **controllo in parallelo** selezionare il pulsante **Mostra solo thread** con flag ![Mostra thread con flag](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Solo i thread contrassegnati vengono visualizzati nell'elenco.

    > [!TIP]
    > Dopo aver contrassegnato alcuni thread, è possibile fare clic con il pulsante destro del mouse su una riga di codice nell'editor del codice e scegliere **Esegui thread contrassegnati per il cursore**. Assicurarsi di scegliere il codice che tutti i thread contrassegnati raggiungeranno. In Visual Studio i thread vengono sospesi sulla riga di codice selezionata, semplificando il controllo dell'ordine di esecuzione tramite il [blocco e lo sblocco dei thread](#bkmk_freeze).

4. Selezionare nuovamente il pulsante **Mostra solo thread contrassegnati** per visualizzare di nuovo la modalità **Mostra tutti i thread** .

5. Per deselezionare i thread, fare clic con il pulsante destro del mouse su uno o più thread con flag nella finestra espressione di **controllo in parallelo** e selezionare **Rimuovi flag**.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a>Blocca e sblocca l'esecuzione del thread

> [!TIP]
> È possibile bloccare e sbloccare (sospendere e riprendere) thread per controllare l'ordine in cui i thread eseguono il lavoro. Questo può aiutare a risolvere i problemi di concorrenza, ad esempio i deadlock e le race condition.

1. Nella finestra espressione di **controllo in parallelo** , con tutte le righe selezionate, fare clic con il pulsante destro del mouse e selezionare **blocca**.

    Nella seconda colonna viene visualizzata un'icona di sospensione per ogni riga. L'icona di pausa indica che il thread è bloccato.

2. Deselezionare tutte le altre righe selezionando solo una riga.

3. Fare clic con il pulsante destro del mouse su una riga e selezionare **Sblocca**.

    L'icona Sospendi viene disattivata in questa riga, a indicare che il thread non è più bloccato.

4. Passare all'editor di codice e premere **F11**. Viene eseguito solo il thread non bloccato.

    L'app può anche creare un'istanza di alcuni nuovi thread. I nuovi thread sono senza flag e non sono bloccati.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a>Segui un singolo thread con punti di interruzione condizionali

Può essere utile seguire l'esecuzione di un singolo thread nel debugger. Un modo per eseguire questa operazione consiste nel bloccare i thread a cui non si è interessati. In alcuni scenari potrebbe essere necessario seguire un singolo thread senza bloccare altri thread, ad esempio per riprodurre un bug specifico. Per seguire un thread senza bloccare altri thread, è necessario evitare di suddividere il codice ad eccezione del thread a cui si è interessati. A tale scopo, è possibile impostare un punto di [interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

È possibile impostare punti di interruzione in condizioni diverse, ad esempio il nome del thread o l'ID del thread. Potrebbe essere utile impostare la condizione sui dati che si conoscono è univoca per ogni thread. Si tratta di uno scenario di debug comune, in cui si è più interessati a un particolare valore di dati rispetto a un particolare thread.

1. Fare clic con il pulsante destro del mouse sul punto di interruzione creato in precedenza e selezionare **condizioni**.

2. Nella finestra **Impostazioni** del punto di interruzione immettere `data == 5` per l'espressione condizionale.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Se si è più interessati a un thread specifico, usare un nome di thread o un ID di thread per la condizione. A tale scopo, nella finestra impostazioni del punto di **interruzione** selezionare **filtro** anziché **espressione condizionale**e seguire i suggerimenti per il filtro. È possibile assegnare un nome ai thread nel codice dell'app, in quanto gli ID dei thread cambiano al riavvio del debugger.

3. Chiudere la finestra impostazioni del punto di **interruzione** .

4. Selezionare il pulsante Riavvia ![app](../debugger/media/dbg-tour-restart.png "RestartApp") riavvia per riavviare la sessione di debug.

    Si interromperà il codice sul thread in cui il valore della variabile dati è 5. Nella finestra espressione di **controllo in parallelo** cercare la freccia gialla che indica il contesto del debugger corrente.

5. A questo punto, è possibile eseguire l'istruzione/routine del codice (**F10**) e passare al codice (**F11**) e seguire l'esecuzione del singolo thread.

    Finché la condizione del punto di interruzione è univoca per il thread e il debugger non ha raggiunto altri punti di interruzione su altri thread (potrebbe essere necessario disabilitarli), è possibile eseguire un'istruzione/routine del codice ed eseguire un'istruzione nel codice senza passare ad altri thread.

    > [!NOTE]
    > Quando si avanza il debugger, vengono eseguiti tutti i thread. Tuttavia, il debugger non si interrompe nel codice su altri thread, a meno che uno degli altri thread non raggiunga un punto di interruzione.

## <a name="see-also"></a>Vedi anche

- [Eseguire il debug di applicazioni multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Procedura: utilizzare la finestra stack in parallelo](../debugger/using-the-parallel-stacks-window.md)
- [Procedura: Usare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)