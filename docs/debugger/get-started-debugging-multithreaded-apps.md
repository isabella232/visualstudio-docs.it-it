---
title: Informazioni sul debug di applicazioni multithreading
description: Eseguire il debug usando le finestre Stack in parallelo e Espressioni di controllo parallele in Visual Studio
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 17ce0ac5667c3e44d16f01f9493a16c77aa1c7cd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139033"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Introduzione al debug di applicazioni multithreading (C#, Visual Basic, C++)

Visual Studio fornisce diversi strumenti ed elementi dell'interfaccia utente che consentono di eseguire il debug di applicazioni multithreading. Questa esercitazione illustra come usare marcatori di thread, la finestra **Stack** in parallelo, **la** finestra Espressione di controllo parallela, i punti di interruzione condizionali e i punti di interruzione del filtro. Completando questa esercitazione si acquisiranno familiarità con Visual Studio funzionalità per il debug di applicazioni multithreading.

Questi due argomenti forniscono informazioni aggiuntive sull'uso di altri strumenti di debug multithreading:

- Per usare la barra **degli strumenti Percorso di** debug e la finestra **Thread,** vedere Procedura dettagliata: Eseguire il debug di [un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

- Per un esempio che usa <xref:System.Threading.Tasks.Task> (codice gestito) e il runtime di concorrenza (C++), vedere [procedura dettagliata: Debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md). Per suggerimenti generali sul debug che si applicano alla maggior parte dei tipi di applicazione multithreading, leggere sia questo argomento che questo argomento.

È prima necessario un progetto di applicazione multithreading. Di seguito è riportato un esempio.

## <a name="create-a-multithreaded-app-project"></a>Creare un progetto di app multithreading

1. Aprire Visual Studio e creare un nuovo progetto.

   ::: moniker range=">=vs-2019"

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

   Nella finestra iniziale scegliere **Crea un nuovo progetto**.

   Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#**, **C++** o **Visual Basic** dall'elenco Linguaggio e quindi scegliere Windows **dall'elenco** Piattaforma. 

   Dopo aver applicato il linguaggio e i filtri della piattaforma, scegliere il modello **App console** per .NET Core o C++ e quindi scegliere **Avanti.**

   > [!NOTE]
   > Se il modello corretto non è visualizzato, passare **a** Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo multipiattaforma .NET Core** o Sviluppo desktop con **C++,** quindi **scegliere Modifica**.

   Nella finestra **Configura il nuovo progetto** digitare o immettere *MyThreadWalkthroughApp* nella Project **nome.** Scegliere quindi Avanti **o** **Crea,** a seconda dell'opzione disponibile.

   Per un progetto .NET Core, scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Nella barra dei menu superiore scegliere **File**  >  **nuovo**  >  **Project**. Nel riquadro sinistro della finestra **di dialogo Nuovo** progetto scegliere quanto segue:

   - Per un'app C#, in **Visual C#** scegliere **Windows Desktop** e quindi nel riquadro centrale scegliere App console **(.NET Framework).**
   - Per un Visual Basic app, in Visual Basic **scegliere** **Windows Desktop** e quindi nel riquadro centrale scegliere App console **(.NET Framework).**
   - Per un'app C++, **in Visual C++** scegliere **Windows Desktop** e quindi scegliere Windows Applicazione **console**.

   Se non viene visualizzata l'app **console (.NET Framework)** per, per C++, il modello di progetto **App console,** passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo desktop .NET** o Sviluppo di desktop con **C++,** quindi scegliere **Modifica**.

   Digitare quindi un nome come *MyThreadWalkthroughApp* e fare clic su **OK.**

   Selezionare **OK**.
   ::: moniker-end

   Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il file di origine potrebbe essere *denominato Program.cs*, *MyThreadWalkthroughApp.cpp* o *Module1.vb*.

1. Eliminare il codice visualizzato nel file di origine e sostituirlo con l'elenco di codice di esempio appropriato riportato di seguito.

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

1. Scegliere **Save All** (Salva tutto) dal menu **File**.

1. (solo Visual Basic) Nel Esplora soluzioni (riquadro destro) fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**. Nella scheda **Applicazione** modificare l'oggetto **Di avvio** in **Semplice.**

## <a name="debug-the-multithreaded-app"></a>Eseguire il debug dell'app multithreading

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

1. Fare clic con il pulsante sinistro del mouse sul margine sinistro `Thread.Sleep` dell'istruzione o per inserire un nuovo punto di `std::this_thread::sleep_for` interruzione.

    Nella grondaia, un cerchio rosso indica che in questa posizione è impostato un punto di interruzione.

2. Scegliere **Avvia** debug **(** **F5)** dal menu Debug .

    Visual Studio compila la soluzione, l'app inizia a essere eseguita con il debugger collegato e quindi l'app viene arrestata in corrispondenza del punto di interruzione.

3. Nell'editor del codice sorgente individuare la riga che contiene il punto di interruzione.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>Individuare il marcatore del thread  

1. Nella barra degli strumenti Debug selezionare il **pulsante Mostra thread nell'origine** Mostra ![thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Premere **F11 una** volta per far avanzare il debugger di una riga di codice.

3. All'estrema sinistra della finestra, In questa riga verrà visualizzata l'icona del *marcatore* thread  ![Marcatore](../debugger/media/dbg-thread-marker.png "ThreadMarker") thread simile a due thread contorti. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Un marcatore di thread può essere parzialmente nascosto da un punto di interruzione.

4. Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati che indica il nome e il numero ID thread per ogni thread arrestato. In questo caso, il nome è probabilmente `<noname>` .

5. Selezionare il marcatore thread per visualizzare le opzioni disponibili nel menu di scelta rapida.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>Visualizzare i percorsi dei thread

Nella finestra **Stack in parallelo** è possibile passare dalla visualizzazione Thread alla visualizzazione Attività (per la programmazione basata su attività) e visualizzare le informazioni sullo stack di chiamate per ogni thread. In questa app è possibile usare la visualizzazione Thread.

1. Aprire la **finestra Stack in** parallelo scegliendo **Debug** Windows  >    >  **Stack paralleli**. Verrà visualizzato un messaggio simile al seguente. Le informazioni esatte variano a seconda della posizione corrente di ogni thread, dell'hardware e del linguaggio di programmazione.

    ![Finestra Stack paralleli](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In questo esempio, da sinistra a destra vengono visualizzate queste informazioni per il codice gestito:

    - Il thread principale (lato sinistro) è stato arrestato in , dove il punto di arresto è indicato dall'icona marcatore `Thread.Start` ![thread Marcatore thread](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Due thread sono stati inseriti in , uno dei quali `ServerClass.InstanceMethod` è il thread corrente (freccia gialla), mentre l'altro thread è stato arrestato in `Thread.Sleep` .
    - Anche un nuovo thread (a destra) viene avviato ma viene arrestato in `ThreadHelper.ThreadStart` .

2. Fare clic con il pulsante destro del mouse sulle voci nella finestra **Stack paralleli** per visualizzare le opzioni disponibili nel menu di scelta rapida.

    È possibile eseguire varie azioni da questi menu di scelta rapida, ma per questa esercitazione verranno visualizzati altri dettagli nella finestra **Controllo** parallelo (sezioni successive).

    > [!NOTE]
    > Per visualizzare una visualizzazione elenco con informazioni su ogni thread, usare invece la **finestra** Thread. Vedere [Procedura dettagliata: Eseguire il debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Impostare un controllo su una variabile

1. Aprire la **finestra Espressioni di controllo** in parallelo selezionando **Debug**  >  **Windows** Parallel  >  **Watch** Parallel  >  **Watch 1**.

2. Selezionare la cella in cui viene visualizzato il testo (o la cella di intestazione vuota `<Add Watch>` nella 4a colonna) e immettere `data` .

    I valori per la variabile di dati per ogni thread vengono visualizzati nella finestra.

3. Selezionare la cella in cui viene visualizzato il testo (o la cella di `<Add Watch>` intestazione vuota nella 5a colonna) e immettere `count` .

    I valori per la `count` variabile per ogni thread vengono visualizzati nella finestra. Se queste informazioni non sono ancora visualizzate, provare a premere **F11** alcune volte per far avanzare l'esecuzione dei thread nel debugger.

    ![Finestra Espressioni di controllo in parallelo](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Fare clic con il pulsante destro del mouse su una delle righe nella finestra per visualizzare le opzioni disponibili.

### <a name="flag-and-unflag-threads"></a>Impostare e rimuovere i flag dei thread
È possibile contrassegnare i thread per tenere traccia dei thread importanti e ignorare gli altri thread.

1. Nella finestra **Controllo parallelo** tenere premuto **MAIUSC** e selezionare più righe.

2. Fare clic con il pulsante destro del mouse e **scegliere Contrassegna**.

    Tutti i thread selezionati vengono contrassegnati. A questo punto, è possibile filtrare per visualizzare solo i thread contrassegnati.

3. Nella finestra **Controllo parallelo** selezionare il pulsante Mostra solo **thread contrassegnati** ![Mostra thread contrassegnati](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Nell'elenco vengono visualizzati solo i thread contrassegnati.

    > [!TIP]
    > Dopo aver contrassegnato alcuni thread, è possibile fare clic con il pulsante destro del mouse su una riga di codice nell'editor di codice e scegliere Esegui thread **contrassegnati nel cursore**. Assicurarsi di scegliere il codice che tutti i thread contrassegnati raggiungeranno. Visual Studio thread verranno sospesi nella riga di codice selezionata, rendendo più semplice controllare l'ordine di esecuzione bloccando e [scosciando i thread](#bkmk_freeze).

4. Selezionare di **nuovo il pulsante Mostra solo thread contrassegnati** per tornare alla modalità Mostra tutti **i** thread.

5. Per annullare il flag dei thread, fare clic  con il pulsante destro del mouse su uno o più thread contrassegnati nella finestra Controllo parallelo e **scegliere Annulla flag**.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Bloccare e scoscire l'esecuzione del thread

> [!TIP]
> È possibile bloccare e scoscire (sospendere e riprendere) i thread per controllare l'ordine in cui i thread eseguono il lavoro. Ciò consente di risolvere i problemi di concorrenza, ad esempio deadlock e race conditions.

1. Nella finestra **Controllo parallelo,** con tutte le righe selezionate, fare clic con il pulsante destro del mouse e scegliere **Blocca**.

    Nella seconda colonna viene visualizzata un'icona di sospensione per ogni riga. L'icona di sospensione indica che il thread è bloccato.

2. Deselezionare tutte le altre righe selezionando una sola riga.

3. Fare clic con il pulsante destro del mouse su una riga **e scegliere Thaw**.

    L'icona di sospensione si allontana in questa riga, a indicare che il thread non è più bloccato.

4. Passare all'editor di codice e premere **F11.** Viene eseguito solo il thread non bloccato.

    L'app può anche creare un'istanza di alcuni nuovi thread. Tutti i nuovi thread non sono flagged e non sono bloccati.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> Seguire un singolo thread con punti di interruzione condizionali

Può essere utile seguire l'esecuzione di un singolo thread nel debugger. Un modo per eseguire questa operazione è bloccare i thread a cui non si è interessati. In alcuni scenari potrebbe essere necessario seguire un singolo thread senza bloccare altri thread, ad esempio per riprodurre un bug specifico. Per seguire un thread senza bloccare altri thread, è necessario evitare di suddividere il codice, ad eccezione del thread a cui si è interessati. A tale scopo, impostare un punto di [interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

È possibile impostare punti di interruzione in condizioni diverse, ad esempio il nome del thread o l'ID del thread. Può essere utile impostare la condizione sui dati che si sa essere univoci per ogni thread. Si tratta di uno scenario di debug comune, in cui si è più interessati a un determinato valore di dati rispetto a qualsiasi thread specifico.

1. Fare clic con il pulsante destro del mouse sul punto di interruzione creato in precedenza e **scegliere Condizioni.**

2. Nella finestra **Impostazioni** punto di interruzione immettere `data == 5` per l'espressione condizionale.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Punto di interruzione condizionale")

    > [!TIP]
    > Se si è più interessati a un thread specifico, usare un nome di thread o un ID thread per la condizione. A tale scopo, nella finestra **Impostazioni**  punto di interruzione selezionare Filtro anziché **Espressione** condizionale e seguire i suggerimenti per il filtro. È possibile assegnare un nome ai thread nel codice dell'app, in quanto gli ID dei thread cambiano quando si riavvia il debugger.

3. Chiudere la finestra **di dialogo Impostazioni** punto di interruzione.

4. Selezionare il pulsante ![Riavvia riavvia l'app](../debugger/media/dbg-tour-restart.png "RestartApp") per riavviare la sessione di debug.

    Si interrompe il codice nel thread in cui il valore della variabile dati è 5. Nella finestra **Espressioni di controllo** in parallelo cercare la freccia gialla che indica il contesto del debugger corrente.

5. È ora possibile eseguire il codice un'istruzione alla volta (**F10**) ed eseguire un'istruzione nel codice (**F11**) e seguire l'esecuzione del thread singolo.

    Se la condizione del punto di interruzione è univoca per il thread e il debugger non ha raggiunto altri punti di interruzione in altri thread (potrebbe essere necessario disabilitarli), è possibile eseguire il codice ed eseguire un'istruzione alla volta senza passare ad altri thread.

    > [!NOTE]
    > Quando si fa avanzare il debugger, verranno eseguiti tutti i thread. Tuttavia, il debugger non interrompe il codice in altri thread a meno che uno degli altri thread non raggiunge un punto di interruzione.

## <a name="see-also"></a>Vedi anche

- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Procedura: Usare la finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)
- [Procedura: Usare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)