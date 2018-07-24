---
title: Informazioni su come eseguire il debug di applicazioni multithreading
description: Eseguire il debug usando le finestre Espressioni di controllo parallelo e stack in parallelo in Visual Studio
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a037ef99a7e1ea56f6535b99b533c1c723fd2d81
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204219"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Iniziare il debug di applicazioni multithreading in Visual Studio
Visual Studio offre diversi strumenti e gli elementi dell'interfaccia utente per il debug di applicazioni multithreading. Questa esercitazione illustra come usare i marcatori dei thread, il **stack in parallelo** finestra, il **espressioni di controllo parallela** finestra punti di interruzione condizionali e i punti di interruzione di filtro. Questa esercitazione richiede solo pochi minuti, ma il suo completamento consentirà di familiarizzare con le funzionalità per il debug di applicazioni multithreading.

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) sul debug con multithreading che illustra una procedura simile. |

Altri argomenti forniscono informazioni aggiuntive sull'uso di altri strumenti di debug con multithreading:

- Per un argomento simile che mostra come usare il **posizione di Debug** sulla barra degli strumenti e il **thread** finestra, vedere [procedura dettagliata: Debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

- Per un argomento simile con un esempio che usa <xref:System.Threading.Tasks.Task> (codice gestito) e il runtime di concorrenza (C++), vedere [questa procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md). Per suggerimenti di debug generali applicabili a tipi di applicazioni più a thread multipli, leggere questo argomento sia l'argomento collegato.
  
Prima di iniziare questa esercitazione, è necessario un progetto di applicazione a thread multipli. Per creare tale progetto, attenersi alla procedura qui indicata.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Per creare il progetto di app a thread multipli  
  
1.  Nel **File** menu, scegliere **New** e quindi fare clic su **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Nel **tipo di progetto**s, scegliere il linguaggio di propria scelta: **Visual c#**, **Visual C++**, oppure **Visual Basic**.  
  
3.  Nel **modelli** , scegliere **App Console**.  
  
4.  Nel **nome** casella, digitare il nome MyThreadWalkthroughApp.  
  
5.  Fare clic su **OK**.  
  
     Verrà visualizzato un nuovo progetto console. Dopo aver creato il progetto, viene visualizzato un file di origine. A seconda del linguaggio scelto, il file di origine potrebbe essere chiamato Module1.vb, Program.cs o MyThreadWalkthroughApp. cpp.  
  
6.  Eliminare il codice riportato nel file di origine e sostituirlo con il codice di esempio illustrato di seguito.

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
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
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
  
7.  Nel **File** menu, fare clic su **Salva tutto**.  
  
#### <a name="to-begin-the-tutorial"></a>Per iniziare l'esercitazione  
  
-   Nell'editor del codice sorgente, cercare il codice seguente: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Per avviare il debug  
  
1.  Fare clic sul margine a sinistra del `Thread.Sleep` o `this_thread::sleep_for` istruzione per inserire un nuovo punto di interruzione.  
  
     Nella barra di navigazione sul lato sinistro dell'editor del codice sorgente, viene visualizzato un cerchio rosso. che indica l'impostazione di un punto di interruzione in tale posizione. 
  
2.  Nel **Debug** menu, fare clic su **Avvia debug** (**F5**).  
  
     Visual Studio compila la soluzione, l'app viene avviata l'esecuzione con il debugger collegato e quindi l'app si arresta nel punto di interruzione.  
  
    > [!NOTE]
    > Se si passa lo stato attivo alla finestra della console, fare clic nella [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per restituire lo stato attivo alla finestra [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Nell'editor del codice sorgente, individuare la riga che contiene il punto di interruzione:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Per individuare il marcatore del thread  

1.  Nella barra degli strumenti di Debug, scegliere il **Mostra thread nell'origine** pulsante ![Mostra thread nell'origine](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Premere **F11** una volta per far avanzare la riga di un debugger del codice.
  
3.  All'estrema sinistra della finestra, In questa riga, si noterà una *marcatore del thread* icona ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") che due fili. Il marcatore del thread indica l'interruzione di un thread in questa posizione.

    Si noti che un marcatore del thread potrebbe essere parzialmente nascosta da un punto di interruzione. 
  
4.  Posizionare il puntatore del mouse sul marcatore del thread. Viene visualizzato un suggerimento dati. in cui è indicato il nome e il numero ID di ciascun thread interrotto. In questo caso, il nome è probabilmente `<noname>`. 
  
5.  Fare clic sul marcatore del thread per visualizzare le opzioni disponibili nel menu di scelta rapida.
    
## <a name="ParallelStacks"></a>Consente di visualizzare il percorso di thread

Nel **stack in parallelo** finestra, è possibile passare tra una visualizzazione thread e (per la programmazione basata su attività) Visualizza le attività e si possono visualizzare informazioni sullo stack di chiamate per ogni thread. In questa app, è possibile usare la visualizzazione dei thread.

1. Aprire il **stack in parallelo** finestra scegliendo **Debug > Windows > stack in parallelo**. Dovrebbe essere simile al seguente (le informazioni esatte sarà diverse a seconda della posizione corrente di ogni thread, l'hardware e il linguaggio di programmazione).

    ![Finestra Stack in parallelo](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    In questo esempio, da sinistra a destra è ottenere queste informazioni per il codice gestito:
    
    - Il thread principale (lato sinistro) è stato arrestato sul `Thread.Start` (il punto di interruzione è indicato dall'icona marcatore thread ![marcatore del Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Due thread di avere immesso il `ServerClass.InstanceMethod`, uno dei quali è il thread corrente (freccia gialla), mentre l'altro thread è stato arrestato `Thread.Sleep`.
    - È inoltre avviare un nuovo thread (sulla destra) (stato arrestato sul `ThreadHelper.ThreadStart`).

2.  Mouse nel **stack in parallelo** finestra per visualizzare le opzioni disponibili nel menu di scelta rapida.

    È possibile eseguire varie azioni da questi menu di scelta rapida, ma per questa esercitazione verrà illustrato più di questi dettagli nel **espressioni di controllo parallela** finestra (sezioni).

    > [!NOTE]
    > Se si è più interessati a visualizzare un elenco consente di visualizzare informazioni su ogni thread, usare il **thread** finestra invece. Visualizzare [procedura dettagliata: Debug di un'applicazione multithreading](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Impostare un'espressione di controllo in una variabile

1. Aprire il **espressioni di controllo parallela** finestra scegliendo **Debug > Windows > espressioni di controllo parallela > parallele espressioni di controllo 1**.

2. Fare clic nella cella in cui vengono visualizzate le `<Add Watch>` testo o la cella di intestazione vuota nella colonna 4 °, tipo `data`, e premere INVIO.

    Nella finestra vengono visualizzati i valori per la variabile di dati per ogni thread.

3. Fare nuovamente clic nella cella in cui vengono visualizzate le `<Add Watch>` testo (o la cella di intestazione vuota nella colonna 5), tipo `count`, quindi premere INVIO.

    Nella finestra vengono visualizzati i valori per la variabile di conteggio per ogni thread. (Se non viene visualizzato ancora così tante informazioni, provare a premere F11 altre volte per passare l'esecuzione dei thread nel debugger.)

    ![Finestra Espressioni di controllo in parallelo](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Fare doppio clic su una delle righe della finestra per visualizzare le opzioni disponibili.

## <a name="flagging-and-unflagging-threads"></a>Impostazione e rimozione dei flag dei thread  
È possibile contrassegnare i thread che si desidera prestare particolare attenzione. Contrassegnare i thread è un buon metodo per tenere traccia dei thread importanti e per ignorare i thread che non è rilevante.  
  
#### <a name="to-flag-threads"></a>Per impostare i flag dei thread  

1. Nel **espressioni di controllo parallela** finestra, tenere premuto il tasto MAIUSC e selezionare più righe.

2. Pulsante destro del mouse e scegliere **Flag**.

    A questo punto, tutti i thread selezionati vengono contrassegnati. A questo punto, è possibile filtrare per mostrare solo thread con flag.
  
3.  Nel **espressioni di controllo parallela** finestra, trovare il **Mostra solo thread con flag** pulsante ![Mostra thread con flag](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Scegliere il **Mostra solo thread con flag** pulsante.  
  
    Nell'elenco viene visualizzato ora solo il thread con flag.

    > [!TIP]
    > Quando si hanno alcuni thread con flag, è possibile fare doppio clic su una riga di codice nell'editor del codice e scegliere **eseguire i thread con flag fino al cursore** (assicurarsi che si sceglie di codice che tutti i thread con flag raggiungeranno). Questo verrà messo in pausa thread nella riga selezionata di codice, rendendo più semplice controllare l'ordine di esecuzione da [blocco e sblocco dei thread](#bkmk_freeze).

5.  Scegliere il **Mostra solo thread con flag** pulsante per tornare alla **Mostra tutti i thread** modalità.
    
#### <a name="to-unflag-threads"></a>Per rimuovere i flag dei thread

Per rimuovere i flag dei thread, è possibile fare doppio clic su uno o più thread con flag nel **espressioni di controllo parallela** finestra e scegliere **Rimuovi flag**.

## <a name="bkmk_freeze"></a> Blocco e sblocco dell'esecuzione del thread 

> [!TIP]
> È possibile bloccare e sbloccare (sospendere e riprendere) i thread per controllare l'ordine in cui i thread di eseguono operazioni. Ciò consente di risolvere i problemi di concorrenza, ad esempio i deadlock e race condition.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Per bloccare e sbloccare i thread  
  
1.  Nel **espressioni di controllo parallela** finestra, con tutte le righe selezionate, pulsante destro del mouse e selezionare **Freeze**.

    Nella seconda colonna, Sospendi a questo punto viene visualizzata un'icona per ogni riga. L'icona di sospensione indica che il thread è bloccato.

2.  Deselezionare le righe, fare clic su una sola riga.

3.  Fare doppio clic su una riga e selezionare **Sblocca**.

    L'icona di sospensione viene chiuso in questa riga, che indica che il thread non è più bloccato.

4.  Passare all'editor del codice e fare clic su **F11**. Viene eseguito solo il thread non bloccato.

    L'app può anche creare un'istanza di alcuni nuovi thread. Si noti che tutti i nuovi thread senza flag e non sono bloccati.

## <a name="bkmk_follow_a_thread"></a> Seguire un singolo Thread usando i punti di interruzione condizionale

In alcuni casi, può essere utile seguire l'esecuzione di un singolo thread nel debugger. A tale scopo, è possibile bloccare i thread che non si sono interessati, ma in alcuni scenari è preferibile seguire un solo thread senza bloccare altri thread (per riprodurre il bug di un particolare, ad esempio). Per eseguire un thread senza bloccare altri thread, è necessario evitare l'interruzione del codice, ad eccezione nel thread in cui si è interessati. È possibile farlo impostando un [punto di interruzione condizionale](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

È possibile impostare i punti di interruzione in condizioni diverse, ad esempio il nome del thread o l'ID del thread. Un altro metodo che può essere utile consiste nell'impostare la condizione su dati che già conosci sarà univoca per ogni thread. Si tratta di uno scenario di debug comune, in cui è più interessati a un valore di dati specifico rispetto in qualsiasi thread specifico.

#### <a name="to-follow-a-single-thread"></a>Per seguire un singolo thread

1. Il pulsante destro del punto di interruzione creato in precedenza e scegliere **condizioni**.

2. Nel **impostazioni punto di interruzione** (finestra), tipo `data == 5` per l'espressione condizionale.

    ![Punto di interruzione condizionale](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Se è più interessati a un thread specifico, usare un nome del thread o un ID di thread per la condizione. Per eseguire questa operazione **impostazioni punto di interruzione** finestra, seleziona **filtro** anziché **espressione condizionale**e seguire i suggerimenti di filtro. È possibile denominare i thread nel codice dell'app (perché gli ID thread cambiare al riavvio del debugger).

3. Chiudi il **impostazioni punto di interruzione** finestra.

4. Fare clic su di riavvio ![App riavviare](../debugger/media/dbg-tour-restart.png "RestartApp") per riavviare la sessione di debug.

    Interromperà nel codice sul thread per il quale la variabile di dati è 5. Cercare la freccia gialla (contesto del debugger corrente) **espressioni di controllo parallela** finestra per verificare che.

5. A questo punto, è possibile saltare il codice (F10) e l'istruzione nel codice (F11) e seguire l'esecuzione del thread singolo.

    Finché la condizione di punto di interruzione è univoca per il thread e il debugger non raggiungere qualsiasi altro punto di interruzione in altri thread (potrebbe essere necessario disabilitare le), è possibile saltare il codice e l'istruzione nel codice senza dover passare agli altri thread.

    > [!NOTE]
    > Quando si arriva il debugger, verranno eseguiti tutti i thread. Tuttavia, il debugger non interrompe nel codice in altri thread, a meno che uno degli altri thread raggiunge un punto di interruzione. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Informazioni sulle finestre di debug multithread 

#### <a name="to-switch-to-another-thread"></a>Per passare a un altro thread 

- Per passare a un altro thread, vedere [procedura: passare a un altro Thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Per altre informazioni sulle finestre Stack paralleli ed espressioni di controllo parallela  
  
- Vedere [procedura: usare la finestra Stack paralleli](../debugger/using-the-parallel-stacks-window.md) 

- Vedere [procedura: utilizzare la finestra Espressioni di controllo parallela](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura: Passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)
