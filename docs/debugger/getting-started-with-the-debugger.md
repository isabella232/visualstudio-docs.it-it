---
title: Informazioni sul debug tramite il debugger di Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1629e98c6d0afa4d259b7b983d1efe0633321c13
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468728"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>: Esercitazione eseguire il debug usando Visual Studio

Questo articolo presenta le funzionalità del debugger di Visual Studio in una procedura dettagliata. Se si desidera una visualizzazione di alto livello delle funzionalità di debug, vedere [Debugger Feature Tour](../debugger/debugger-feature-tour.md). Quando si *il debug dell'app*, in genere significa che si esegue l'applicazione con il debugger collegato. Quando si esegue questa operazione, il debugger fornisce diversi modi per ottenere informazioni sulle attività del codice mentre è in esecuzione. È possibile esaminare il codice ed esaminare i valori archiviati nelle variabili, è possibile impostare espressioni di controllo sulle variabili per vedere quando i valori cambiano, è possibile esaminare il percorso di esecuzione del codice, vedere se un ramo del codice è in esecuzione e così via. Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sull'esecuzione del debug che illustra una procedura simile. |

Anche se l'app demo è c# e C++, le funzionalità sono applicabili a Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (se diversamente specificato). Gli screenshot sono in c#.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avviare il debugger e raggiungere punti di interruzione.
> * Informazioni sui comandi per avanzare nel codice nel debugger
> * Ispezione delle variabili nelle finestre del debugger e i suggerimenti dati
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio 2017 installato e il **sviluppo desktop .NET** oppure **sviluppo Desktop con C++** carico di lavoro.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto** (selezionare **File** > **Nuovo** > **Progetto**). Verrà avviato il Programma di installazione di Visual Studio. Scegliere il. **Sviluppo di applicazioni desktop NET** o **sviluppo Desktop con C++** carico di lavoro, quindi scegliere **Modify**.

## <a name="create-a-project"></a>Creare un progetto

1. In Visual Studio scegliere **File > Nuovo progetto**.

2. Sotto **Visual c#** oppure **Visual C++**, scegliere **Windows Desktop**, quindi nel riquadro centrale scegliere **App Console** ( **Applicazione Console Windows** in C++).

    Se non viene visualizzato il **applicazione Console** modello di progetto, fare clic sul **aperto Visual Studio Installer** collegamento nel riquadro sinistro della finestra di **nuovo progetto** nella finestra di dialogo. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il *sviluppo di applicazioni desktop .NET** o **sviluppo Desktop con C++** carico di lavoro, quindi scegliere **Modify**.

3. Digitare un nome come **get-avviato-Debug** e fare clic su **OK**.

    Visual Studio crea il progetto.

4. Nelle *Program.cs* (c#) o *get-avviato-debugging.cpp* (C++), sostituire il codice seguente

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;

    namespace get_started_debugging
    {
        class Program
        {
            static void Main(string[] args)
            {
            }
        }
    }
    ```

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con questo codice:

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Shape
    {
        // A few example members
        public int X { get; private set; }
        public int Y { get; private set; }
        public int Height { get; set; }
        public int Width { get; set; }
   
        // Virtual method
        public virtual void Draw()
        {
            Console.WriteLine("Performing base class drawing tasks");
        }
    }

    class Circle : Shape
    {
        public override void Draw()
        {
            // Code to draw a circle...
            Console.WriteLine("Drawing a circle");
            base.Draw();
        }
    }

    class Rectangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle");
            base.Draw();
        }
    }

    class Triangle : Shape
    {
        public override void Draw()
        {
            // Code to draw a triangle...
            Console.WriteLine("Drawing a trangle");
            base.Draw();
        }
    }

    class Program
    {
        static void Main(string[] args)
        {

            var shapes = new List<Shape>
            {
                new Rectangle(),
                new Triangle(),
                new Circle()
            };

            foreach (var shape in shapes)
            {
                shape.Draw();
            }

            // Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
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

1. Premere **F5** (**Debug > Avvia debug**) o nella **Avvia debug** pulsante ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug ") nella barra degli strumenti Debug.

     **F5** avvia l'app con il debugger collegato all'app di elaborare, ma ora è stata ancora eseguita alcuna operazione particolare per esaminare il codice. Quindi, solo caricamento dell'app e viene visualizzato l'output della console.

    ```
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     In questa esercitazione verranno Esaminiamo più da vicino l'app usando il debugger e ottenere un quadro il debugger di funzionalità.

2. Arrestare il debugger premendo l'arresto rossa ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "arresta debug") pulsante.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

1. Nel `foreach` ciclo del `Main` funzione (`for` ciclo in C++ `main` (funzione)), impostare un punto di interruzione facendo clic sul margine sinistro della prima riga del codice.

    ![Impostare un punto di interruzione](../debugger/media/get-started-set-breakpoint.png "SetABreakPoint")

    Viene visualizzato un cerchio rosso in cui è impostato il punto di interruzione.

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. 

6. Premere **F5** o nella **Avvia debug** pulsante, l'app viene avviata e il debugger viene eseguito per la riga di codice in cui è impostato il punto di interruzione.

    ![Raggiungere un punto di interruzione](../debugger/media/get-started-hit-breakpoint.png "HitABreakPoint")

    La freccia gialla rappresenta l'istruzione in cui il debugger ha sospeso, che anche sospende l'esecuzione di app nella stessa fase (questa istruzione non è ancora eseguito).

     Se l'app non è ancora in esecuzione, **F5** viene avviato il debugger e si interrompe al primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app per il punto di interruzione successivo.

    I punti di interruzione sono una funzionalità molto utile quando si conosce la riga di codice o nella sezione di codice che si desidera esaminare in dettaglio.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di passaggio

In genere, usiamo i tasti di scelta rapida in questo caso, perché è un buon metodo per ottenere rapidamente in esecuzione l'app nel debugger (comandi equivalenti, ad esempio menu i comandi vengono visualizzati tra parentesi).

1. Premere **F11** (oppure scegliere **Debug > Esegui istruzione**) una volta (più volte in c#) fino a quando non si posiziona sul `shape.Draw` chiamata al metodo il `Main` metodo (`shape->Draw` in C++).

1. Premere **F11** ancora una volta per far avanzare nel codice per il `Rectangle` classe.

     ![Usare F11 per codice Esegui istruzione](../debugger/media/get-started-f11.png "F11 Esegui istruzione")

     F11 è il **Esegui istruzione** comando e sposta in avanti l'app esecuzione un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nella maggior parte dei dettagli. (Per spostare più velocemente tramite il codice, viene illustrato alcune altre opzioni inoltre.) Per impostazione predefinita, il debugger ignora codice non utente (se si desidera visualizzare ulteriori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

2. Premere **F10** (oppure scegliere **Debug > Esegui istruzione/routine**) più volte fino a quando il debugger si arresta nel `base.Draw` chiamata al metodo (`Shape::Draw` in C++), quindi premere **F10** Ancora una volta.

     ![Usare F10 per codice Esegui istruzione/routine](../debugger/media/get-started-step-over.png "F10 Esegui istruzione/routine")

     Si noti che questa volta che il debugger non eseguirne il `Draw` metodo della classe di base (`Shape`). **F10** fa avanzare il debugger senza eseguire istruzioni di funzioni o metodi nel codice dell'app (il codice viene ancora eseguito). Premendo F10 il `base.Draw` (o `Shape::Draw`) chiamata al metodo (anziché **F11**), viene ignorato il codice di implementazione per `base.Draw` (quali ad esempio se si non sta interessano subito).

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con Esegui fino al clic

5. Nell'editor del codice, scorrere verso il basso e passare il mouse sul `Console.WriteLine` metodo (`std::cout` in C++) nel `Triangle` classe fino al verde **eseguire fa clic su** pulsante ![eseguire fa clic su] (../debugger/media/dbg-tour-run-to-click.png " RunToClick") viene visualizzata a sinistra.

     ![Usare l'esecuzione a fare clic su funzionalità](../debugger/media/get-started-run-to-click.png "eseguire fa clic su")

    >  [!NOTE]
    > Il **Esegui fino al clic** pulsante è stato introdotto in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se non viene visualizzata sul pulsante freccia verde, usare **F11** in questo esempio invece di far avanzare il debugger nel posto giusto.

6. Fare clic sul **Esegui fino al fare clic su** pulsante ![Esegui fino al fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Tramite questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. **Esegui fino al clic** è utile per ottenere rapidamente all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

    Fa avanzare il debugger di `Console.WriteLine` implementazione del metodo per il `Triangle` classe (`std::cout` in C++).

    Durante la pausa, si nota un errore di digitazione. L'output "Disegno un trangle" è errato. Per poterlo correggere qui durante l'esecuzione dell'app nel debugger.

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

1. Fare clic su "Disegno un trangle" e digitare una correzione, la modifica di "trangle" a "triangle".

1. Premere **F11** una sola volta e viene visualizzato che anticipi nuovamente il debugger.

    > [!NOTE]
    > A seconda di quale tipo di codice si modifica nel debugger, è possibile vedere un messaggio di avviso. In alcuni scenari, il codice sarà necessario ricompilare prima di continuare.

## <a name="step-out"></a>Esci da istruzione

Si supponga di che aver esaminando il `Draw` metodo nel `Triangle` classe e si vuole ricavare la funzione, ma rimangono nel debugger. È possibile farlo usando il **Esci da istruzione /** comando.

1. Premere **Shift** + **F11** (o **Debug > Esci da istruzione**).

     Questo comando riprende l'esecuzione di app (e fa avanzare il debugger) fino a quando non restituisce la funzione corrente.

     Verrà visualizzata nuovamente la `foreach` ciclo nella `Main` metodo (`for` ciclo in C++).

## <a name="restart-your-app-quickly"></a>Riavviare l'app rapidamente

Fare clic sui **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") pulsante sulla barra degli strumenti Debug (**Ctrl** + **MAIUSC**   +  **F5**).

Quando si preme **riavviare**, consentono di risparmiare tempo e l'arresto dell'app e riavviare il debugger. Il debugger si fermerà in corrispondenza il primo punto di interruzione viene raggiunto mediante l'esecuzione di codice.

Il debugger si arresta nuovamente nel punto di interruzione è impostato, nelle `foreach` ciclo (`for` ciclo in C++).

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Funzionalità che consentono di controllare le variabili sono una delle funzionalità più utili del debugger, ed esistono diversi modi per farlo. Spesso, quando si tenta di eseguire il debug di un problema, si sta tentando di scoprire se le variabili archiviano i valori che si prevede possano avere in un determinato momento.

1. Durante la pausa nel `foreach` ciclo (`for` ciclo in C++), premere **F11** una volta.

1. Passare il mouse sul `shapes` oggetto e viene visualizzato il valore di proprietà predefinito, il `Count` proprietà.

1. Espandere la `shapes` oggetto per visualizzare tutte le relative proprietà, ad esempio il primo indice della matrice `[0]`, che ha il valore di `Rectangle` (c#) o un indirizzo di memoria (C++).

     ![Visualizzare un suggerimento dati](../debugger/media/get-started-data-tip.png "consente di visualizzare un suggerimento dati")

    Spesso, durante il debug, si desidera un modo rapido per verificare i valori delle proprietà sugli oggetti e i suggerimenti dati sono un buon metodo per eseguire questa operazione.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e variabili locali

1. Esaminare i **Auto** finestra nella parte inferiore dell'editor del codice.

     ![Esaminare le variabili nella finestra Auto](../debugger/media/get-started-autos-window.png "finestra Auto")

    Nel **Auto** finestra, noterete che le variabili e il relativo valore corrente. Il **Auto** finestra Mostra tutte le variabili usate nella riga corrente o nella riga precedente (In C++, la finestra Mostra le variabili in tre righe di codice precedenti. Vedere la documentazione per il comportamento specifico del linguaggio).

    > [!NOTE]
    > In JavaScript, il **variabili locali** finestra è supportata ma non le **Auto** finestra.

2. Esaminare quindi le **variabili locali** accanto a una scheda della finestra di **Auto** finestra.

    Il **variabili locali** finestra Mostra le variabili presenti nell'attuale [ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)).

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra dell'editor di codice principale, fare doppio clic il `shapes` dell'oggetto e scegli **Aggiungi espressione di controllo**.

    Il **Watch** verrà visualizzata la finestra nella parte inferiore dell'editor del codice. È possibile usare una **Watch** per specificare una variabile (o un'espressione) che si desidera tenere d'occhio nella finestra.

    A questo punto, si dispone di un'espressione di controllo impostato sul `shapes` oggetto ed è possibile visualizzarne il valore cambia quando sposta tramite il debugger. A differenza di altre finestre delle variabili, il **Watch** finestra Mostra sempre le variabili che sta controllando (è disattivati quando fuori ambito).

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

1. Durante la pausa il `foreach` ciclo (`for` ciclo in C++), fare clic sui **Stack di chiamate** finestra, per impostazione predefinita è aperto nel riquadro inferiore destro.

1. Fare clic su **F11** alcune volte finché non viene visualizzato il debugger di sospendere le risorse nel `Circle.Draw` metodo nell'editor del codice. Esaminare i **Stack di chiamate** finestra.

    ![Esaminare lo stack di chiamate](../debugger/media/get-started-call-stack.png "ExamineCallStack")

    Il **Stack di chiamate** finestra Mostra l'ordine in cui vengono introduzione chiamate i metodi e le funzioni. La prima riga visualizza la funzione corrente (il `Circle.Draw` o `Circle::Draw` metodo nell'app). La seconda riga indica che `Circle.Draw` è stato chiamato dal `Main` metodo (`main` in C++) e così via.

    >  [!NOTE]
    > Il **Stack di chiamate** finestra è simile alla prospettiva di Debug in alcuni ambienti di sviluppo integrato, ad esempio Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per passare osservare che il codice sorgente e che viene modificato anche l'ambito corrente viene controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida dal **Stack di chiamate** finestra per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione in funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore**e passare a esaminare il codice sorgente. Per altre informazioni, vedere [procedura: esaminare lo Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Il debugger è in pausa nel `Circle.Draw` chiamata al metodo, premere due volte **F11** più volte fino a quando il debugger viene sospesa in corrispondenza di `base.Draw` chiamata al metodo (`Shape::Draw` in C++).

1. Utilizzare il mouse per selezionare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla alto di una riga per il `Console.WriteLine` (`std::cout` in C++) chiamata al metodo.

1. Premere **F11** ancora una volta.

    Il debugger consente di rieseguire il `Console.WriteLine` metodo (`std::cout` in C++).

    Se si modifica il flusso di esecuzione, è possibile eseguire operazioni come percorsi di esecuzione di codice diversi di test o eseguire di nuovo codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso è necessario prestare attenzione con questa funzionalità, e viene visualizzato un avviso nella descrizione comando. È possibile visualizzare altri avvisi, troppo. Spostare il puntatore del mouse non è possibile ripristinare l'applicazione a uno stato precedente di app.

1. Premere **F5** per continuare l'esecuzione dell'app.

    L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger oltre a collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
