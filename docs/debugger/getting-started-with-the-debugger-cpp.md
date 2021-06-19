---
title: 'Esercitazione: Eseguire il debug del codice C++'
description: Informazioni sulle funzionalità del debugger Visual Studio e su come avviare il debugger, esaminare il codice ed esaminare i dati in un'applicazione C++.
ms.custom: debug-experiment,  get-started
ms.date: 02/04/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8abb517103254aa1e0c89a02b0dc81b38af3ecee
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385253"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Esercitazione: Informazioni sul debug del codice C++ tramite Visual Studio

Questo articolo descrive le funzionalità del debugger di Visual Studio con una procedura dettagliata. Per una panoramica di alto livello delle funzionalità del debugger, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md). Quando si esegue il *debug dell'app* in genere si esegue l'applicazione con il debugger collegato. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile rivedere il codice ed esaminare i valori archiviati nelle variabili, impostare espressioni di controllo nelle variabili per rilevare le modifiche dei valori, esaminare il percorso di esecuzione del codice, verificare l'esecuzione di un ramo del codice e così via. Se è la prima volta che si esegue il debug del codice, può essere utile leggere [Debug per principianti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

Anche se l'app demo è C++, la maggior parte delle funzionalità è applicabile a C#, Visual Basic, F#, Python, JavaScript e altri linguaggi supportati da Visual Studio (F# non supporta Modifica e continuazione. F# e JavaScript non supportano la finestra **Auto**). Gli screenshot sono in C++.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avvio del debugger e raggiungimento dei punti di interruzione
> * Uso dei comandi per esaminare il codice nel debugger
> * Ispezione delle variabili nelle finestre dei suggerimenti dati e del debugger
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

È necessario che siano installati Visual Studio 2019 e il carico di lavoro **Sviluppo di applicazioni desktop con C++**.

::: moniker-end
::: moniker range="vs-2017"

È necessario che siano installati Visual Studio 2017 e il carico di lavoro **Sviluppo di applicazioni desktop con C++**.

::: moniker-end

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2022"

Se non è già stato installato Visual Studio 2022 Preview, passare alla pagina di download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarla gratuitamente.

::: moniker-end

Se è necessario installare il carico di lavoro ma Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++**, quindi scegliere **Modifica**.

## <a name="create-a-project"></a>Creare un progetto

In primo luogo, si creerà un progetto di applicazione console C++. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu superiore scegliere **File** > **nuovo** > **progetto**.

3. Nella finestra **di dialogo Nuovo** progetto nel riquadro sinistro espandere Visual C++ e quindi scegliere Desktop di **Windows**.  Nel riquadro centrale scegliere Applicazione **console di Windows**. Assegnare quindi al progetto il *nome get-started-debugging*.

     Se il modello di progetto **App** console non è visualizzato, scegliere il collegamento **Apri** Programma di installazione di Visual Studio nel riquadro sinistro della **finestra** di dialogo Nuovo progetto. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

4. Fare clic su **OK**.

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio 2019.

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C++ dall'elenco** Linguaggio e quindi **windows dall'elenco** Piattaforma. 

   Dopo aver applicato i filtri della lingua e della piattaforma, scegliere il modello **App console** e quindi **scegliere Avanti.**

   ![Scegliere il modello C++ per l'app console](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Se il modello App **console** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Nella finestra di dialogo Programma di installazione di Visual Studio quindi scegliere il carico di lavoro **Sviluppo desktop con C++.**

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *get-started-debugging* nella **casella Nome** progetto . Scegliere quindi **Crea**.

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creazione dell'applicazione

1. In *get-started-debugging.cpp* sostituire tutto il codice predefinito con il codice seguente:

    ```cpp
    #include <string>
    #include <vector>
    #include <iostream>

    void SendMessage(const std::wstring& name, int msg)
    {
        std::wcout << L"Hello, " << name << L"! Count to " << msg << std::endl;
    }

    int main()
    {
        std::vector<wchar_t> letters = { L'f', L'r', L'e', L'd', L' ', L's', L'm', L'i', L't', L'h' };
        std::wstring name = L"";
        std::vector<int> a(10);
        std::wstring key = L"";

        for (int i = 0; i < letters.size(); i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        std::wcin >> key;
        return 0;
    }
    ```

## <a name="start-the-debugger"></a>Avviare il debugger.

1. Premere **F5** (**Debug > Avvia** debug ) o il pulsante Avvia debug ![Avvia](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") debug sulla barra degli strumenti debug. 

     **F5** avvia l'app con il debugger collegato al processo dell'app. Fino ad ora, tuttavia, non è stata eseguita alcuna operazione per esaminare il codice. Di conseguenza, viene semplicemente avviata l'app e viene visualizzato l'output della console.

    ```cmd
    Hello, f! Count to 1
    Hello, fr! Count to 2
    Hello, fre! Count to 3
    Hello, fred! Count to 4
    Hello, fred ! Count to 5
    Hello, fred s! Count to 6
    Hello, fred sm! Count to 7
    Hello, fred smi! Count to 8
    Hello, fred smit! Count to 9
    Hello, fred smith! Count to 10
    ```

     In questa esercitazione viene esaminata l'app usando il debugger e vengono descritte le funzionalità del debugger.

2. Arrestare il debugger premendo il pulsante rosso Arresta ![debug](../debugger/media/dbg-tour-stop-debugging.png "Debug") (**MAIUSC**  +  **F5**).

3. Nella finestra della console premere un tasto e **INVIO** per chiudere la finestra della console.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

1. Nel ciclo `for` della funzione `main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `name += letters[i];`

    Viene visualizzato un punto di ![interruzione](../debugger/media/dbg-breakpoint.png "Punto di interruzione") con cerchio rosso nel punto in cui si imposta il punto di interruzione.

    I punti di interruzione sono una delle funzionalità di base ed essenziali del debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

2. Premere **F5 o il** pulsante **Avvia** debug Avvia debug ![,](../debugger/media/dbg-tour-start-debugging.png "Avvia debug")l'app viene avviata e il debugger viene eseguito sulla riga di codice in cui è stato impostato il punto di interruzione.

    ![Impostare e raggiungere un punto di interruzione](../debugger/media/get-started-set-breakpoint-cpp.png)

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

     Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio. Per informazioni sui diversi tipi di punti di interruzione che è possibile impostare, ad esempio i punti di interruzione condizionali, vedere [Uso dei punti di interruzione](../debugger/using-breakpoints.md).

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di esecuzione

In questa esercitazione nella maggior parte dei casi vengono usati tasti di scelta rapida che rappresentano un modo rapido per eseguire l'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono indicati tra parentesi).

1. Durante la sospensione nel ciclo nel metodo, premere `for` `main` **F11** (o scegliere Debug > Esegui istruzione ) due volte per passare alla chiamata `SendMessage` al metodo.

     Dopo aver **premuto F11** due volte, si dovrebbe essere in questa riga di codice:

     `SendMessage(name, a[i]);`

1. Premere **F11** ancora una volta per eseguire un'istruzione al `SendMessage` metodo.

     Il puntatore giallo avanza nel `SendMessage` metodo .

     ![Usare F11 per eseguire un'istruzione al codice](../debugger/media/get-started-f11-cpp.png "F10 Step Into")

     F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. Per spostarsi più velocemente nel codice, vengono mostrate anche alcune altre opzioni. Per impostazione predefinita, il debugger ignora il codice non utente (per altri dettagli, [vedere Just My Code](../debugger/just-my-code.md)).

     Si immagini di aver esaminato il metodo e di voler uscire dal metodo ma rimanere `SendMessage` nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere **MAIUSC**  +  **F11** (o **Eseguire il debug > istruzione/uscita**).

     Questo comando riprende l'esecuzione dell'app (e fa avanzare il debugger) finché non viene restituito il metodo o la funzione corrente.

     È necessario tornare nel `for` ciclo nel metodo , sospeso alla chiamata al metodo `main` `SendMessage` .

1. Premere **F11** più volte finché non si torna di nuovo alla `SendMessage` chiamata al metodo.

1. Mentre è in pausa durante la chiamata al metodo, premere **F10** (o **scegliere Debug > esegui istruzione/istruzione**) una sola volta.

     ![Usare F10 per eseguire il passaggio del codice](../debugger/media/get-started-step-over-cpp.png "F10 Step Over")

     Si noti che questa volta il debugger non esegue un'istruzione nel `SendMessage` metodo . **F10** fa avanzare il debugger senza eseguire le istruzioni nelle funzioni o nei metodi del codice dell'app (il codice rimane in esecuzione). Premendo **F10** nella chiamata al metodo `SendMessage` anziché **F11**, è stato ignorato il codice di implementazione per `SendMessage` (non d'interesse ai fini dell'esercitazione). Per altre informazioni sui diversi modi per spostarsi nel codice, vedere [Esplorare il codice nel debugger](../debugger/navigating-through-code-with-the-debugger.md).

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con il pulsante per l'esecuzione fino alla riga selezionata dall'utente

1. Premere **F5 per** passare al punto di interruzione.

1. Nell'editor di codice scorrere verso il basso e passare il puntatore del mouse sulla funzione nel metodo fino a quando a sinistra non viene visualizzato il pulsante verde Esegui per fare clic `std::wcout` sul pulsante Esegui per fare `SendMessage` clic.  ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick") La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

     ![Usare la funzionalità Esegui per fare clic](../debugger/media/get-started-run-to-click-cpp.png "Esegui fino alla riga selezionata")

   > [!NOTE]
   > Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è una nuova funzionalità di [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se il pulsante freccia verde non è visualizzato, usare **F11** in questo esempio per far avanzare il debugger nella posizione giusta.

2. Fare clic **sul pulsante Esegui fino a fare** clic sul pulsante Esegui fino a fare clic ![su](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Il debugger passa alla `std::wcout` funzione .

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

Fare clic sul **pulsante Restart** ![Restart App (Riavvia](../debugger/media/dbg-tour-restart.png "RestartApp") riavvia app) sulla barra degli strumenti di debug (**CTRL**  +    +  **MAIUSC+F5).**

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente in corrispondenza del punto di interruzione impostato in precedenza all'interno del `for` ciclo .

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Mentre è in pausa nell'istruzione , passare il mouse sulla variabile per visualizzare `name += letters[i]` `letters` il valore predefinito, `size={10}` .

1. Espandere la `letters` variabile per visualizzarne le proprietà, che includono tutti gli elementi contenuti nella variabile.

1. Passare quindi il puntatore `name` sulla variabile per visualizzarne il valore corrente, una stringa vuota.

1. Premere **F5** (o **Continua** debug ) alcune volte per eseguire l'iterazione più volte nel ciclo, sospendo nuovamente in corrispondenza del punto di interruzione e passando il puntatore sulla variabile ogni volta per controllarne il  >   `for` `name` valore.

     ![Visualizzare un suggerimento dati](../debugger/media/get-started-data-tip-cpp.png "Visualizzare un suggerimento dati")

     Il valore della variabile cambia a ogni iterazione del ciclo, visualizzando i valori `for` di , quindi , e così `f` `fr` `fre` via.

     Spesso, durante il debug, è necessario controllare rapidamente i valori delle proprietà sulle variabili, per vedere se si stanno archiviando i valori previsti, e i suggerimenti dati costituiscono un valido strumento per questa operazione.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

    Se è chiuso, aprirlo mentre è in pausa nel debugger scegliendo **Debug**  >  **Finestre**  >  **Auto.**

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. La finestra **Auto** mostra tutte le variabili usate nella riga corrente o nella riga precedente (vedere la documentazione per il comportamento specifico del linguaggio).

1. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

1. Espandere la `letters` variabile per visualizzare gli elementi in essa contenuti.

     ![Esaminare le variabili nella finestra Variabili locali](../debugger/media/get-started-locals-window-cpp.png "finestra Variabili locali")

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione corrente.

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra principale dell'editor di codice fare clic con il pulsante destro del mouse `name` sulla variabile e scegliere Aggiungi espressioni di **controllo**.

    Viene visualizzata la finestra **Espressione di controllo** nella parte inferiore dell'editor di codice. È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

    A questo punto, è disponibile un'orologio impostato sulla variabile ed è possibile visualizzarne la modifica del valore mentre `name` si passa attraverso il debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** mostra sempre le variabili controllate (che appaiono disattivate quando sono fuori ambito).

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

1. Mentre l'esecuzione è in pausa nel ciclo `for`, fare clic sulla finestra **Stack di chiamate**, visualizzata per impostazione predefinita nel riquadro inferiore destro.

    Se è chiuso, aprirlo mentre è in pausa nel debugger scegliendo **Debug Stack di** chiamate  >    >  **Windows**.

2. Fare **clic su F11** alcune volte fino a quando il debugger non viene sospeso nel `SendMessage` metodo . Osservare la finestra **Stack di chiamate**.

    ![Esaminare lo stack di chiamate](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `SendMessage` in questa app). La seconda riga indica che `SendMessage` è stato chiamato dal metodo `main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Premere **F11** due volte per eseguire la `std::wcout` funzione.

1. Con il debugger sospeso nella chiamata al metodo, usare il mouse per afferrare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla verso l'alto di una riga, di nuovo `SendMessage` su `std::wcout` .

1. Premere **F11**.

    Il debugger riesegui la `std::wcout` funzione (come si può vedere nell'output della finestra della console).

    Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Non è possibile ripristinare uno stato precedente dell'applicazione spostando il cursore.

1. Premere **F5** per continuare a eseguire l'app.

    L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)

