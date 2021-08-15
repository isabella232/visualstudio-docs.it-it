---
title: Analizzare i dati di utilizzo della CPU (ASP.NET Core)
description: Misurare le prestazioni delle app nelle ASP.NET Core usando lo strumento di diagnostica Utilizzo CPU
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
- aspnet
ms.openlocfilehash: 1f34ed0a68c4fb8f26421a69d27dbfbd86069a3d19e6b79b91f209bf8636b930
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442183"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet-core"></a>Guida introduttiva: Analizzare i dati di utilizzo della CPU Visual Studio (ASP.NET Core)

Visual Studio dispone di molte funzionalità avanzate per l'analisi dei problemi di prestazioni nell'applicazione. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base. In questo caso si esamina uno strumento che identifica eventuali colli di bottiglia delle prestazioni a causa di un utilizzo intensivo della CPU. Gli strumenti di diagnostica sono supportati per lo sviluppo di .NET in Visual Studio, incluso ASP.NET, e per lo sviluppo nativo/C++.

L'hub diagnostica include numerose altre opzioni per eseguire e gestire la sessione di diagnostica. Se lo strumento **Utilizzo CPU** descritto qui non offre i dati necessari, gli [altri strumenti di profilatura](../profiling/profiling-feature-tour.md) mettono a disposizione diversi tipi di informazioni che possono risultare utili. In molti casi il collo di bottiglia delle prestazioni dell'applicazione può dipendere da un fattore diverso dalla CPU, ad esempio la memoria, il rendering dell'interfaccia utente o il tempo di richiesta di rete. [PerfTips,](../profiling/perftips.md)un altro strumento di profilatura integrato nel debugger, consente anche di eseguire il codice un'istruzione alla volta e di identificare il tempo necessario per il completamento di determinate funzioni o blocchi di codice.

Per Windows 8 e versioni successive è necessario eseguire gli strumenti di profilatura con il debugger, nella finestra **Strumenti di diagnostica**. In Windows 7 e versioni successive, è possibile usare lo strumento di relazione finale, il [profiler delle prestazioni](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Creare un progetto

1. Aprire Visual Studio e creare il progetto.

   ::: moniker range="vs-2017"
   Nella barra dei menu superiore scegliere **File** > **Nuovo** > **Project**.

   Nella finestra **di Project** nuova applicazione nel riquadro sinistro espandere **Visual C#** e quindi scegliere **Web.** Nel riquadro centrale scegliere ASP.NET **Web (.NET Core)**. Assegnare quindi al progetto il *MyProfilingApp_MVC*.

   > [!NOTE]
   > Se il modello di progetto Applicazione **Web ASP.NET (.NET Core)** non è visualizzato, scegliere il collegamento Apri **Programma di installazione di Visual Studio** nel riquadro sinistro della finestra di **dialogo Project** nuova applicazione. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web** e quindi scegliere **Modifica**.

   Nella finestra di dialogo visualizzata scegliere **MVC** nel riquadro centrale e quindi fare clic su **OK**.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **File**  >  **Start Window (Finestra iniziale file)** e quindi **Scegliere Create a new project (Crea un nuovo progetto).**

   Digitare **app Web** nella casella di ricerca, scegliere **C#** come linguaggio, scegliere ASP.NET Core Applicazione **Web (Model-View-Controller)** e quindi scegliere **Avanti.** Nella schermata successiva assegnare al *progetto* MyProfilingApp_MVC e quindi scegliere **Avanti.**

   Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**

   > [!NOTE]
   > Se il modello Applicazione **Web ASP.NET (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra Crea **un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. A questo punto scegliere il carico di lavoro **Sviluppo ASP.NET e Web** nel programma di installazione di Visual Studio.
   ::: moniker-end

   Visual Studio crea e apre il nuovo progetto.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella Models e **scegliere Aggiungi**  >  **classe.**

1. Assegnare alla nuova classe il nome `Data.cs` e scegliere **Aggiungi**.

1. In Esplora soluzioni aprire `Models/Data.cs` e aggiungere la seguente istruzione `using` all'inizio del file:

    ```csharp
    using System.Threading;
    ```

1. In Data.cs sostituire il codice seguente:

    ```csharp
    public class Data
    {
    }
    ```

    Con questo:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
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
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. In Esplora soluzioni aprire *Controller/HomeControllers.cs* e sostituire il codice seguente:

   ::: moniker range="vs-2017"

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    Con questo:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

    ::: moniker-end
    ::: moniker range=">=vs-2019"

    ```csharp
    public IActionResult Privacy()
    {
        return View();
    }
    ```

    Con questo:

    ```csharp
    public IActionResult Privacy()
    {
        Models.Simple s = new Models.Simple();

        return View(s.GetData());
    }
    ```

    ::: moniker-end


## <a name="step-1-collect-profiling-data"></a>Passaggio 1: Raccogliere i dati di profilatura

1. In primo luogo impostare un punto di interruzione dell'app su questa riga di codice nel costruttore `Simple`:

    `for (int i = 0; i < 200; i++)`

    Per impostare un punto di interruzione fare clic sul margine a sinistra della riga di codice.

1. Impostare quindi un secondo punto di interruzione sulla parentesi graffa di chiusura alla fine del costruttore `Simple`:

     ![Impostare i punti di interruzione per la profilatura](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    Impostando i due punti di interruzione è possibile limitare la raccolta dei dati per le parti di codice che si vuole analizzare.

1. La finestra **Strumenti di diagnostica** è già visibile, a meno che non sia stata disattivata. Per visualizzare nuovamente la finestra, fare clic su  >  **Debug Windows** Mostra  >  **Strumenti di diagnostica**.

1. Fare **clic su Debug**  >  **Avvia** debug (o Avvia sulla barra degli strumenti o **F5).** 

1. Al termine del caricamento dell'app, fare clic sul collegamento appropriato nella parte superiore della pagina Web per avviare l'esecuzione del nuovo codice.

   ::: moniker range="vs-2017"
   In Visual Studio 2017 fare clic sul **collegamento Informazioni** su per eseguire il codice.
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   In Visual Studio 2019 fare clic sul **collegamento Privacy** per eseguire il codice.
   ::: moniker-end

1. Viene visualizzata la vista **Riepilogo** degli strumenti di diagnostica.

1. Quando il debugger è in pausa, abilitare la raccolta dei dati relativi all'utilizzo della CPU scegliendo **Registra profilo CPU**, quindi aprire la scheda **Utilizzo CPU**.

     ![Abilitazione profilatura CPU in Strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-summary.png)

     Quando la raccolta dei dati è abilitata, il pulsante di registrazione visualizza un cerchio rosso.

     Quando si sceglie **Registra profilo CPU** Visual Studio inizia a registrare le funzioni e il tempo necessario per l'esecuzione e crea un grafico della sequenza temporale, utile per concentrarsi su segmenti specifici della sessione di campionamento. È possibile visualizzare i dati raccolti solo quando l'esecuzione dell'applicazione si interrompe in corrispondenza di un punto di interruzione.

6. Premere F5 per eseguire l'applicazione fino al secondo punto di interruzione.

     Ora si hanno a disposizione i dati relativi alle prestazioni per l'applicazione, precisamente per l'area di codice compresa tra i due punti di interruzione.

     Il profiler inizia a preparare i dati di thread. Attendere il completamento.

     Lo strumento Utilizzo CPU consente di visualizzare il report nella scheda **Utilizzo CPU**.

     A questo punto, è possibile iniziare ad analizzare i dati.

## <a name="step-2-analyze-cpu-usage-data"></a>Passaggio 2: Analizzare i dati di utilizzo della CPU

È consigliabile iniziare ad analizzare i dati esaminando l'elenco di funzioni in Utilizzo CPU, identificando le funzioni che svolgono la maggior parte del lavoro e quindi concentrandosi su ognuna di esse.

1. Nell'elenco delle funzioni esaminare le funzioni che eseguono il maggior numero di operazioni.

     ![Scheda Utilizzo CPU in Strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Le funzioni sono elencate in ordine a partire da quelle che svolgono la maggior parte del lavoro (non sono in ordine di chiamata). Ciò consente di identificare rapidamente le funzioni in esecuzione da più tempo.

2. Nell'elenco delle funzioni fare doppio clic sulla funzione `MyProfilingApp_MVC.Models.ServerClass::GetNumber`.

    Quando si fa doppio clic su una funzione viene aperta la visualizzazione **Chiamante/chiamato** nel riquadro a sinistra.

    ![Visualizzazione Chiamante/chiamato in Strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    In questa visualizzazione la funzione selezionata viene visualizzata nell'intestazione e nella casella **Funzione corrente** (in questo esempio `ServerClass::GetNumber`). La funzione che ha chiamato la funzione corrente viene visualizzata a sinistra, sotto **Funzioni chiamanti**, e tutte le funzioni chiamate dalla funzione corrente sono riportate nella casella **Funzioni chiamate** sulla destra. Selezionare una delle due caselle per modificare la funzione corrente.

    Questa visualizzazione indica il tempo totale (ms) e la percentuale del tempo complessivo di esecuzione dell'applicazione dedicato al completamento della funzione.

    **Corpo funzione** indica anche la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. In questo esempio 2220 ms su 2235 sono stati usati per il corpo della funzione e il tempo rimanente (inferiore a 20 ms) per il codice esterno chiamato dalla funzione. I valori reali saranno diversi a seconda dell'ambiente.

    > [!TIP]
    > Valori elevati in **Corpo funzione** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

## <a name="next-steps"></a>Passaggi successivi

- [Analizzare l'uso della memoria](../profiling/memory-usage.md) per identificare colli di bottiglia delle prestazioni.
- [Analizzare l'uso della CPU](../profiling/cpu-usage.md) per informazioni dettagliate sullo strumento Utilizzo CPU.
- Analizzare l'uso della CPU senza un debugger collegato o usando un'app in esecuzione. Per altre informazioni, vedere [Raccogliere dati di profilatura senza il debug](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) in [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Vedi anche

- [Profilatura in Visual Studio](../profiling/index.yml)
- [Presentazione degli strumenti di profilatura](../profiling/profiling-feature-tour.md)
