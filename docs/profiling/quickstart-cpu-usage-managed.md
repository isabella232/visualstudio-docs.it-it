---
title: Analizzare i dati di utilizzo della CPU (C#, Visual Basic)
description: Misurare le prestazioni delle app in C# e Visual Basic con lo strumento di diagnostica Utilizzo CPU
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: d3902d8119b8de8eba49cf28a7730cc41d505438
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107069"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Guida introduttiva: Analizzare i dati di utilizzo della CPU Visual Studio (C#, Visual Basic)

Visual Studio dispone di molte funzionalità avanzate per l'analisi dei problemi di prestazioni nell'applicazione. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base. In questo caso si esamina lo strumento che identifica eventuali colli di bottiglia delle prestazioni dovuti a un uso intensivo della CPU. Gli strumenti di diagnostica sono supportati per lo sviluppo di .NET in Visual Studio, incluso ASP.NET, e per lo sviluppo nativo/C++.

L'hub diagnostica include numerose altre opzioni per eseguire e gestire la sessione di diagnostica. Se lo strumento **Utilizzo CPU** descritto qui non offre i dati necessari, gli [altri strumenti di profilatura](../profiling/profiling-feature-tour.md) mettono a disposizione diversi tipi di informazioni che possono risultare utili. In molti casi il collo di bottiglia delle prestazioni dell'applicazione può dipendere da un fattore diverso dalla CPU, ad esempio la memoria, il rendering dell'interfaccia utente o il tempo di richiesta di rete. Il Profiler prestazioni offre molte altre opzioni per registrare e analizzare questo tipo di dati. [PerfTips,](../profiling/perftips.md)un altro strumento di profilatura integrato nel debugger, consente anche di eseguire il codice un'istruzione alla volta e di identificare il tempo necessario per il completamento di determinate funzioni o blocchi di codice.

Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**. In Windows 7 e versioni successive, è possibile usare lo strumento di relazione finale, il [profiler delle prestazioni](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Creare un progetto

1. Aprire Visual Studio e creare il progetto.

   ::: moniker range="vs-2017"
   Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

   Nella finestra **di dialogo Project** nel riquadro sinistro espandere **C#** o **Visual Basic** e quindi scegliere **.NET Core.** Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al progetto *il nome MyProfilerApp*.

   Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

   Nella finestra iniziale scegliere **Crea un nuovo progetto.**

   Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#** o **Visual Basic** dall'elenco Linguaggio e quindi scegliere Windows **dall'elenco** Piattaforma .

   Dopo aver applicato i filtri del linguaggio e della piattaforma, scegliere il modello **App** console per .NET Core e quindi **scegliere Avanti.**

   > [!NOTE]
   > Se il modello App **console non viene** visualizzato, è possibile installarlo dalla finestra Crea un **nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.

   Nella finestra **Configura il nuovo progetto** digitare o immettere *MyProfilerApp* nella casella **Project nome.** Scegliere quindi **Avanti.**

   Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**

   ::: moniker-end

   Visual Studio aprirà il nuovo progetto.

2. Aprire *Program.cs* e sostituire tutto il codice con il codice seguente:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > In Visual Basic assicurarsi che l'oggetto di avvio sia impostato su `Sub Main` (**Proprietà** Oggetto di  >  **avvio**  >  **dell'applicazione**).

## <a name="step-1-collect-profiling-data"></a>Passaggio 1: Raccogliere i dati di profilatura

1. In primo luogo impostare un punto di interruzione dell'app su questa riga di codice nella funzione `Main`:

    `for (int i = 0; i < 200; i++)`

    oppure, per Visual Basic:

    `For i As Integer = 0 To 199`

    Per impostare un punto di interruzione fare clic sul margine a sinistra della riga di codice.

2. Impostare quindi un secondo punto di interruzione sulla parentesi graffa di chiusura alla fine della funzione `Main`:

     ![Impostare i punti di interruzione per la profilatura](../profiling/media/quickstart-cpu-usage-breakpoints.png "Impostare i punti di interruzione per la profilatura")

    Impostando i due punti di interruzione è possibile limitare la raccolta dei dati per le parti di codice che si vuole analizzare.

3. La finestra **Strumenti di diagnostica** è già visibile, a meno che non sia stata disattivata. Per visualizzare nuovamente la finestra, fare clic su **Debug**  >  **Windows**  >  **Mostra Strumenti di diagnostica**.

4. Fare **clic su Debug**  >  **Avvia** debug (o Avvia sulla barra degli strumenti o **F5).** 

     Al termine del caricamento dell'applicazione viene visualizzata la vista **Riepilogo** degli strumenti di diagnostica.

5. Quando il debugger è in pausa, abilitare la raccolta dei dati relativi all'utilizzo della CPU scegliendo **Registra profilo CPU**, quindi aprire la scheda **Utilizzo CPU**.

     ![Abilitazione profilatura CPU in Strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-summary.png "Abilitazione profilatura CPU in Strumenti di diagnostica")

     Quando la raccolta dei dati è abilitata, il pulsante di registrazione visualizza un cerchio rosso.

     Quando si sceglie **Registra profilo CPU** Visual Studio inizia a registrare le funzioni e il tempo necessario per l'esecuzione e crea un grafico della sequenza temporale, utile per concentrarsi su segmenti specifici della sessione di campionamento. È possibile visualizzare i dati raccolti solo quando l'esecuzione dell'applicazione si interrompe in corrispondenza di un punto di interruzione.

6. Premere **F5** per eseguire l'applicazione fino al secondo punto di interruzione.

     Ora si hanno a disposizione i dati relativi alle prestazioni per l'applicazione, precisamente per l'area di codice compresa tra i due punti di interruzione.

     Il profiler inizia a preparare i dati di thread. Attendere il completamento.

     Lo strumento Utilizzo CPU consente di visualizzare il report nella scheda **Utilizzo CPU**.

     A questo punto, è possibile iniziare ad analizzare i dati.

## <a name="step-2-analyze-cpu-usage-data"></a>Passaggio 2: Analizzare i dati di utilizzo della CPU

È consigliabile iniziare ad analizzare i dati esaminando l'elenco di funzioni in Utilizzo CPU, identificando le funzioni che svolgono la maggior parte del lavoro e quindi concentrandosi su ognuna di esse.

1. Nell'elenco delle funzioni esaminare le funzioni che eseguono il maggior numero di operazioni.

     ![Scheda Utilizzo CPU degli strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Le funzioni sono elencate in ordine a partire da quelle che svolgono la maggior parte del lavoro (non sono in ordine di chiamata). Ciò consente di identificare rapidamente le funzioni in esecuzione da più tempo.

2. Nell'elenco delle funzioni fare doppio clic sulla funzione `ServerClass::GetNumber`.

    Quando si fa doppio clic su una funzione viene aperta la visualizzazione **Chiamante/chiamato** nel riquadro a sinistra.

    ![Visualizzazione Chiamante/chiamato in Strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    In questa visualizzazione la funzione selezionata viene visualizzata nell'intestazione e nella casella **Funzione corrente** (in questo esempio `GetNumber`). La funzione che ha chiamato la funzione corrente viene visualizzata a sinistra, sotto **Funzioni chiamanti**, e tutte le funzioni chiamate dalla funzione corrente sono riportate nella casella **Funzioni chiamate** sulla destra. Selezionare una delle due caselle per modificare la funzione corrente.

    Questa visualizzazione indica il tempo totale (ms) e la percentuale del tempo complessivo di esecuzione dell'applicazione dedicato al completamento della funzione.

    **Corpo funzione** indica anche la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. In questo esempio 2856 ms su 2863 sono stati usati per il corpo della funzione e il tempo rimanente (inferiore a 20 ms) per il codice esterno chiamato dalla funzione. I valori reali saranno diversi a seconda dell'ambiente.

    > [!TIP]
    > Valori elevati in **Corpo funzione** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

## <a name="next-steps"></a>Passaggi successivi

- [Analizzare l'uso della memoria](../profiling/memory-usage.md) per identificare colli di bottiglia delle prestazioni.
- [Analizzare l'uso della CPU](../profiling/cpu-usage.md) per informazioni dettagliate sullo strumento Utilizzo CPU.
- Analizzare l'uso della CPU senza un debugger collegato o usando un'app in esecuzione. Per altre informazioni, vedere [Raccogliere dati di profilatura senza il debug](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) in [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Vedi anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
