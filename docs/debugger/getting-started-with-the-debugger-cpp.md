---
title: Informazioni sul debug del codice C++ tramite il debugger di Visual Studio
description: Informazioni su come avviare il debugger di Visual Studio, eseguire il codice un'istruzione alla volta ed esaminare i dati.
ms.custom: debug-experiment
ms.date: 08/01/2018
ms.topic: tutorial
dev_langs:
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeef905b2372b22be7aee157c4d0249109ea3749
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725865"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Esercitazione: Informazioni sul debug del codice C++ tramite Visual Studio

Questo articolo descrive le funzionalità del debugger di Visual Studio con una procedura dettagliata. Per una panoramica di alto livello delle funzionalità del debugger, vedere [Presentazione del debugger](../debugger/debugger-feature-tour.md). Quando si esegue il *debug dell'app* in genere si esegue l'applicazione con il debugger collegato. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile rivedere il codice ed esaminare i valori archiviati nelle variabili, impostare espressioni di controllo nelle variabili per rilevare le modifiche dei valori, esaminare il percorso di esecuzione del codice, verificare l'esecuzione di un ramo del codice e così via. Se è la prima volta che si esegue il debug del codice, può essere utile leggere [Debug per principianti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avvio del debugger e raggiungimento dei punti di interruzione
> * Uso dei comandi per esaminare il codice nel debugger
> * Ispezione delle variabili nelle finestre dei suggerimenti dati e del debugger
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

È necessario che siano installati Visual Studio 2019 e il carico di lavoro **Sviluppo di applicazioni desktop con C++** .

::: moniker-end
::: moniker range="vs-2017"

È necessario che siano installati Visual Studio 2017 e il carico di lavoro **Sviluppo di applicazioni desktop con C++** .

::: moniker-end

Se Visual Studio non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads)  per installarlo gratuitamente.

Se occorre installare il carico di lavoro, ma si ha già Visual Studio, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, che apre il programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++** , quindi scegliere **Modifica**.

## <a name="create-a-project"></a>Creare un progetto

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Dalla barra dei menu in alto scegliere **File** > **nuovo** > **progetto**.

3. Nella finestra di dialogo **nuovo progetto** nel riquadro sinistro espandere oggetto **C++visivo**, quindi scegliere desktop di **Windows**. Nel riquadro centrale scegliere **applicazione console di Windows**. Quindi denominare il progetto *Get-Started-Debugging*.

   > [!NOTE]
   > Se il modello di progetto **Applicazione console di Windows** non viene visualizzato, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, aprendo così il programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Selezionare il carico di lavoro **Sviluppo di applicazioni desktop con C++** , quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

   Se la finestra di avvio non è aperta, scegliere **File** > **finestra Start**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere **C++** quindi dall'elenco lingua, quindi scegliere **Windows** dall'elenco piattaforma. 

   Dopo aver applicato la lingua e i filtri della piattaforma, scegliere il modello **applicazione console** e quindi fare clic su **Avanti**.

   ![Scegliere il C# modello per l'app console (.NET Core)](../debugger/media/vs-2019/get-started-create-console-project-cpp.png)

   > [!NOTE]
   > Se il modello di **applicazione console** non è visibile, è possibile installarlo dalla finestra **Crea un nuovo progetto** . Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Quindi, nella programma di installazione di Visual Studio scegliere lo **sviluppo di applicazioni desktop con C++**  carico di lavoro.

1. Nella finestra **Configura nuovo progetto** Digitare o immettere *Get-Started-Debugging* nella casella **nome progetto** . Scegliere **Crea**.

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

1. In *get-started-debugging.cpp* sostituire il codice seguente

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con questo codice:

    ```c++
    #include "pch.h"

    #include <string>
    #include <vector>
    #include <iostream>

    class Shape
    {
        int privateX = 0;
        int privateY = 0;
        int privateHeight = 0;
        int privateWidth = 0;

        int getX() const { return privateX; }
        void setX(int value) { privateX = value; }

        int getY() const { return privateY; }
        void setY(int value) { privateY = value; }

        int getHeight() const { return privateHeight; }
        void setHeight(int value) { privateHeight = value; }

        int getWidth() const { return privateWidth; }
        void setWidth(int value) { privateWidth = value; }

        public:
        // Virtual method
        virtual void Draw()
        {
            std::wcout << L"Performing base class drawing tasks" << std::endl;
        }
    };

    class Circle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a circle...
        std::wcout << L"Drawing a circle" << std::endl;
        Shape::Draw();
        }
    };

    class Rectangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a rectangle...
        std::wcout << L"Drawing a rectangle" << std::endl;
        Shape::Draw();
        }
    };

    class Triangle : public Shape
    {
        public:
        void Draw() override
        {
        // Code to draw a triangle...
        std::wcout << L"Drawing a trangle" << std::endl;
        Shape::Draw();
        }
    };

    int main(std::vector<std::wstring> &args)
    {
        auto shapes = std::vector<Shape*>
        {
            new Rectangle(),
            new Triangle(),
            new Circle()
        };

        for (auto shape : shapes)
        {
            shape->Draw();
        }
    }

    /* Output:
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    */
    ```

## <a name="start-the-debugger"></a>Avviare il debugger.

1. Premere **F5** (**debug > Avvia debug**) o il pulsante **Avvia debug** ![Avvia](../debugger/media/dbg-tour-start-debugging.png "Avvio del debug") debug sulla barra degli strumenti Debug.

     **F5** avvia l'app con il debugger collegato al processo dell'app. Fino ad ora, tuttavia, non è stata eseguita alcuna operazione per esaminare il codice. Di conseguenza, viene semplicemente avviata l'app e viene visualizzato l'output della console.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     In questa esercitazione viene esaminata l'app usando il debugger e vengono descritte le funzionalità del debugger.

2. Arrestare il debugger premendo il pulsante di arresto del ![debug](../debugger/media/dbg-tour-stop-debugging.png "Arresta debug") rosso.

3. Chiudere la finestra della console.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

1. Nel ciclo `for` della funzione `main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `shape->Draw()`

    Quando viene impostato il punto di interruzione viene visualizzato un cerchio rosso.

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

2. Premere **F5** o il pulsante **Avvia debug** ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug". Viene avviata l'app e viene eseguito il debugger fino alla riga di codice in cui è impostato il punto di interruzione.

    ![Impostare e raggiungere un punto di interruzione](../debugger/media/get-started-set-breakpoint-cpp.gif)

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

     Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di esecuzione

In questa esercitazione nella maggior parte dei casi vengono usati tasti di scelta rapida che rappresentano un modo rapido per eseguire l'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono indicati tra parentesi).

1. Mentre l'esecuzione è in pausa nella chiamata al metodo `shape->Draw` nella funzione `main`, premere **F11** (oppure scegliere **Debug > Esegui istruzione**) per avanzare nel codice per la classe `Rectangle`.

     ![Usare F11 per eseguire un'istruzione nel codice](../debugger/media/get-started-f11-cpp.png "Esegui istruzione F11")

     F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. (Per spostarsi più rapidamente tramite codice, vengono mostrate anche altre opzioni). Per impostazione predefinita, il debugger ignora il codice non utente (se si desiderano maggiori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

2. Premere **F10** (oppure scegliere **Debug > Esegui istruzione/routine**) alcune volte fino a quando il debugger non si arresta nella chiamata al metodo `Shape::Draw` e quindi premere **F10** ancora una volta.

     ![Usare F10 per eseguire un'istruzione/routine del codice](../debugger/media/get-started-step-over-cpp.png "Istruzione/routine F10")

     Si noti che questa volta il debugger non esegue l'istruzione nel metodo `Draw` della classe di base (`Shape`). **F10** fa avanzare il debugger senza eseguire le istruzioni nelle funzioni o nei metodi del codice dell'app (il codice rimane in esecuzione). Premendo F10 nella chiamata al metodo `Shape::Draw` anziché **F11**, è stato ignorato il codice di implementazione per `Draw` nella classe di base (non d'interesse ai fini dell'esercitazione).

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con il pulsante per l'esecuzione fino alla riga selezionata dall'utente

1. Fare clic con il pulsante destro del mouse sul punto di interruzione impostato in precedenza e scegliere Elimina punto di **interruzione** oppure premere **Ctrl** + **MAIUSC** + **F9** per eliminare tutti i punti di interruzione.

1. Nell'editor di codice scorrere verso il basso e passare il puntatore del mouse sul `std::cout` nella classe `Triangle` fino a quando non si fa clic sul pulsante verde Esegui **per** fare clic su Visualizza ![a](../debugger/media/dbg-tour-run-to-click.png "RunToClick") sinistra.

     ![Utilizzare la funzionalità Esegui fino al clic](../debugger/media/get-started-run-to-click-cpp.png "Esegui fino alla riga selezionata")

   > [!NOTE]
   > Il pulsante **Esegui fino alla riga selezionata** è disponibile a partire da [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se non viene visualizzato il pulsante freccia verde, usare **F11** in questo esempio invece di far avanzare il debugger fino alla posizione corretta.

2. Fare clic sul pulsante **Esegui fino a fare** clic su ![Esegui](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

    Il debugger avanza fino all'implementazione del metodo `std::cout` per la classe `Triangle`.

    Mentre l'esecuzione è in pausa, si nota un errore di digitazione. L'output "Drawing a trangle" è errato. È possibile correggerlo ora durante l'esecuzione dell'app nel debugger.

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

1. Fare clic su "Drawing a trangle" e digitare una correzione, cambiando "trangle" con "triangle".

1. Premere **F11** una sola volta. Verrà visualizzato un messaggio che informa che è in corso la ricompilazione del codice e quindi il debugger avanza nuovamente.

    > [!NOTE]
    > A seconda del tipo di codice modificato nel debugger, è possibile che venga visualizzato un messaggio di avviso. In alcuni scenari è necessaria la ricompilazione del codice per poter continuare.

## <a name="step-out"></a>Uscire dall'istruzione o dalla routine

Si supponga di aver completato l'esame del metodo `Draw` nella classe `Triangle` e di voler uscire dalla funzione rimanendo nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere **MAIUSC** + **F11** (oppure **Debug > Esci da istruzione/routine**).

     Questo comando riprende l'esecuzione dell'app e fa avanzare il debugger fino alla fine della funzione corrente.

     L'esecuzione dovrebbe tornare al ciclo `for` nel metodo `main`.

1. Fare clic sul margine sinistro per aggiungere un nuovo punto di interruzione nel ciclo `for`.

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

Fare clic sul pulsante **Riavvia** ![app riavvia](../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti Debug (**CTRL** + **MAIUSC** + **F5**).

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente nel punto di interruzione impostato, nel metodo `shape->Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Mentre l'esecuzione è in pausa nel metodo `shape->Draw()`, passare il mouse sul contenitore `shapes` (oggetto vettore) per visualizzare il valore della proprietà predefinita, la proprietà `size`, che mostra `size=3`.

1. Espandere l'oggetto `shapes` per visualizzarne tutte le proprietà, ad esempio il primo indice della matrice `[0]`, che ha un indirizzo di memoria.

    È possibile espandere ulteriormente gli oggetti per visualizzarne le proprietà.

1. Espandere il primo indice `[0]` per visualizzare la proprietà `privateHeight` del rettangolo.

     ![Visualizzare un suggerimento dati](../debugger/media/get-started-data-tip-cpp.png "Visualizzare un suggerimento dati")

     Spesso durante il debug è utile avere a disposizione un modo rapido per controllare i valori delle proprietà negli oggetti e i suggerimenti dati sono un ottimo strumento per eseguire questa operazione.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

     ![Esaminare le variabili nella finestra auto](../debugger/media/get-started-autos-window-cpp.png "Finestra auto")

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. Per C++, la finestra **Auto** mostra le variabili nelle tre righe di codice precedenti.

2. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione del codice corrente.

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra principale dell'editor di codice fare clic con il pulsante destro del mouse sull'oggetto `shapes` e scegliere **Aggiungi espressione di controllo**.

    Viene visualizzata la finestra **Espressione di controllo** nella parte inferiore dell'editor di codice. È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

    Dopo aver impostato l'espressione di controllo nell'oggetto `shapes` è possibile visualizzare la modifica del valore durante gli spostamenti all'interno del debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** mostra sempre le variabili controllate (che appaiono disattivate quando sono fuori ambito).

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

1. Mentre l'esecuzione è in pausa nel ciclo `for`, fare clic sulla finestra **Stack di chiamate**, visualizzata per impostazione predefinita nel riquadro inferiore destro.

2. Fare clic su **F11** alcune volte fino a quando il debugger non viene messo in pausa nel metodo `Shape::Draw` della classe `Rectangle` nell'editor del codice. Osservare la finestra **Stack di chiamate**.

    ![Esaminare lo stack di chiamate](../debugger/media/get-started-call-stack-cpp.png "ExamineCallStack")

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `Rectangle::Draw` in questo esempio). La seconda riga indica che `Rectangle::Draw` è stato chiamato dalla funzione `main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Mentre il debugger è in pausa nella chiamata al metodo `Shape::Draw`, usare il mouse per selezionare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla in alto di una riga alla chiamata al metodo `std::cout`.

1. Premere **F11**.

    Il debugger esegue nuovamente il metodo `std::cout` (visualizzato nell'output della finestra della console).

    Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Non è possibile ripristinare uno stato precedente dell'applicazione spostando il cursore.

1. Premere **F5** per continuare a eseguire l'app.

    L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
