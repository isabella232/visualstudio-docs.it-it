---
title: 'Esercitazione: eseguire il debug del codice Visual Basic'
description: Informazioni su come avviare il debugger di Visual Studio, eseguire il codice un'istruzione alla volta ed esaminare i dati.
ms.custom: debug-experiment, seodec18, get-started
ms.date: 11/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df27ca8ccae6795750dbd1f10b5e1f0199c17330
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76726054"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Esercitazione: Informazioni sul debug del codice Visual Basic tramite Visual Studio

Questo articolo descrive le funzionalità del debugger di Visual Studio con una procedura dettagliata. Per una panoramica di alto livello delle funzionalità del debugger, vedere [Presentazione del debugger](../../debugger/debugger-feature-tour.md). Quando si esegue il *debug dell'app* in genere si esegue l'applicazione con il debugger collegato. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile rivedere il codice ed esaminare i valori archiviati nelle variabili, impostare espressioni di controllo nelle variabili per rilevare le modifiche dei valori, esaminare il percorso di esecuzione del codice, verificare l'esecuzione di un ramo del codice e così via. Se è la prima volta che si esegue il debug del codice, può essere utile leggere [Debug per principianti](../../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avvio del debugger e raggiungimento dei punti di interruzione
> * Uso dei comandi per esaminare il codice nel debugger
> * Ispezione delle variabili nelle finestre dei suggerimenti dati e del debugger
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

È necessario che siano installati Visual Studio 2019 e il carico di lavoro **Sviluppo per desktop .NET**.

::: moniker-end
::: moniker range="vs-2017"

È necessario che siano installati Visual Studio 2017 e il carico di lavoro **Sviluppo per desktop .NET**.

::: moniker-end

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

Se occorre installare il carico di lavoro, ma si ha già Visual Studio, passare a **Strumenti** > **Ottieni strumenti e funzionalità**, che apre il programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.

## <a name="create-a-project"></a>Creare un progetto

In primo luogo, verrà creato un progetto di applicazione console .NET Core. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Dalla barra dei menu in alto scegliere **File** > **nuovo** > **progetto**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Quindi denominare il progetto *Get-Started-Debugging*.

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)** , fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio 2019.

   Se la finestra di avvio non è aperta, scegliere **File** > **finestra Start**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri di linguaggio e piattaforma, scegliere il modello **App console (.NET Core)** e **Avanti**.

   ![Scegliere il C# modello per l'app console (.NET Core)](../../debugger/media/vs-2019/get-started-create-console-project-vb.png)

   > [!NOTE]
   > Se il modello **App console (.NET Core)** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo progetto**. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.

1. Nella finestra **Configura nuovo progetto** Digitare o immettere *Get-Started-Debugging* nella casella **nome progetto** . Scegliere **Crea**.

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

1. In *Module1. vb*sostituire tutto il codice predefinito

    ```vb
    Module Module1

        Sub Main()
        End Sub

    End Module
    ```

    con questo codice:

    ```vb
    Imports System
    Imports System.Collections.Generic

    Public Class Shape

      ' A few example members
        Public Property X As Integer
            Get
                Return X
            End Get
            Set
            End Set
        End Property

        Public Property Y As Integer
            Get
                Return Y
            End Get
            Set
            End Set
        End Property

        Public Property Height As Integer
            Get
                Return Height
            End Get
            Set
            End Set
        End Property

        Public Property Width As Integer
            Get
                Return Width
            End Get
            Set
            End Set
        End Property

        ' Virtual method
        Public Overridable Sub Draw()
            Console.WriteLine("Performing base class drawing tasks")
        End Sub
    End Class

    Public Class Circle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a circle...
            Console.WriteLine("Drawing a circle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Rectangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a rectangle...
            Console.WriteLine("Drawing a rectangle")
            MyBase.Draw()
        End Sub
    End Class

    Public Class Triangle
        Inherits Shape

        Public Overrides Sub Draw()
            ' Code to draw a triangle...
            Console.WriteLine("Drawing a trangle")
            MyBase.Draw()
        End Sub
    End Class

    Module Module1

        Sub Main(ByVal args() As String)

            Dim shapes = New List(Of Shape) From
            {
                New Rectangle,
                New Triangle,
                New Circle
            }

            For Each shape In shapes
                shape.Draw()
            Next
            ' Keep the console open in debug mode.
            Console.WriteLine("Press any key to exit.")
            Console.ReadKey()

        End Sub

    End Module

    ' Output:
    '    Drawing a rectangle
    '    Performing base class drawing tasks
    '    Drawing a triangle
    '    Performing base class drawing tasks
    '    Drawing a circle
    '    Performing base class drawing tasks
    ```

## <a name="start-the-debugger"></a>Avviare il debugger.

1. Premere **F5** (**debug > Avvia debug**) o il pulsante **Avvia debug** ![Avvia](../../debugger/media/dbg-tour-start-debugging.png "Avvio del debug") debug sulla barra degli strumenti Debug.

     **F5** avvia l'app con il debugger collegato al processo dell'app. Fino ad ora, tuttavia, non è stata eseguita alcuna operazione per esaminare il codice. Di conseguenza, viene semplicemente avviata l'app e viene visualizzato l'output della console.

    ```cmd
    Drawing a rectangle
    Performing base class drawing tasks
    Drawing a triangle
    Performing base class drawing tasks
    Drawing a circle
    Performing base class drawing tasks
    ```

     In questa esercitazione viene esaminata l'app usando il debugger e vengono descritte le funzionalità del debugger.

2. Arrestare il debugger premendo il pulsante di arresto del ![debug](../../debugger/media/dbg-tour-stop-debugging.png "Arresta debug") rosso.

3. Chiudere la finestra della console.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

1. Nel ciclo `For Each` della funzione `Main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `shape.Draw()`

    Quando viene impostato il punto di interruzione viene visualizzato un cerchio rosso.

    ![Imposta punto di interruzione](../visual-basic/media/get-started-set-breakpoint-vb.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

2. Premere **F5** o il pulsante **Avvia debug** per ![avviare il debug](../../debugger/media/dbg-tour-start-debugging.png "Avvio del debug"), l'app viene avviata e il debugger viene eseguito fino alla riga di codice in cui è stato impostato il punto di interruzione.

    ![Raggiungere un punto di interruzione](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

     Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di esecuzione

In questa esercitazione nella maggior parte dei casi vengono usati tasti di scelta rapida che rappresentano un modo rapido per eseguire l'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono indicati tra parentesi).

1. Mentre l'esecuzione è in pausa nella chiamata al metodo `shape.Draw` nella funzione `Main`, premere **F11** (oppure scegliere **Debug > Esegui istruzione**) per avanzare nel codice per la classe `Rectangle`.

     ![Usare F11 per eseguire un'istruzione nel codice](../visual-basic/media/get-started-f11-vb.png "Esegui istruzione F11")

     F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. (Per spostarsi più rapidamente tramite codice, vengono mostrate anche altre opzioni). Per impostazione predefinita, il debugger ignora il codice non utente (se si desiderano maggiori dettagli, vedere [Just My Code](../../debugger/just-my-code.md)).

2. Premere **F10** (oppure scegliere **Debug > Esegui istruzione/routine**) alcune volte fino a quando il debugger non si arresta nella chiamata al metodo `MyBase.Draw` e quindi premere **F10** ancora una volta.

     ![Usare F10 per eseguire un'istruzione/routine del codice](../visual-basic/media/get-started-step-over-vb.png "Istruzione/routine F10")

     Si noti che questa volta il debugger non esegue l'istruzione nel metodo `Draw` della classe di base (`Shape`). **F10** fa avanzare il debugger senza eseguire le istruzioni nelle funzioni o nei metodi del codice dell'app (il codice rimane in esecuzione). Premendo **F10** nella chiamata al metodo `MyBase.Draw` anziché **F11**, è stato ignorato il codice di implementazione per `MyBase.Draw` (non d'interesse ai fini dell'esercitazione).

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con il pulsante per l'esecuzione fino alla riga selezionata dall'utente

1. Fare clic con il pulsante destro del mouse sul punto di interruzione impostato in precedenza e scegliere Elimina punto di **interruzione** oppure premere **Ctrl** + **MAIUSC** + **F9** per eliminare tutti i punti di interruzione.

1. Nell'editor di codice scorrere verso il basso e passare il puntatore del mouse sul metodo `Console.WriteLine` nella classe `Triangle` fino a quando non si fa clic **sul pulsante verde Run (** Esegui) per fare ![clic](../../debugger/media/dbg-tour-run-to-click.png "RunToClick") su a sinistra. La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

     ![Utilizzare la funzionalità Esegui fino al clic](../visual-basic/media/get-started-run-to-click-vb.png "Esegui fino alla riga selezionata")

   > [!NOTE]
   > Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è una nuova funzionalità di [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Se non viene visualizzato il pulsante freccia verde, usare **F11** in questo esempio invece di far avanzare il debugger fino alla posizione corretta.

2. Fare clic sul pulsante **Esegui fino a fare** clic su ![Esegui](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

    Il debugger avanza fino all'implementazione del metodo `Console.WriteLine` per la classe `Triangle`. Se il debugger viene sospeso prima in corrispondenza del punto di interruzione impostato in precedenza, utilizzare **Esegui per fare clic** di nuovo per far avanzare il debugger a `Console.WriteLine`.

    Mentre l'esecuzione è in pausa, si nota un errore di digitazione. L'output "Drawing a trangle" è errato. È possibile correggerlo ora durante l'esecuzione dell'app nel debugger.

## <a name="edit-code-and-continue-debugging"></a>Modificare il codice e continuare il debug

1. Fare clic su "Drawing a trangle" e digitare una correzione, cambiando "trangle" con "triangle".

1. Premere **F11** una sola volta per fare in modo che il debugger avanzi nuovamente.

    > [!NOTE]
    > A seconda del tipo di codice modificato nel debugger, è possibile che venga visualizzato un messaggio di avviso. In alcuni scenari è necessaria la ricompilazione del codice per poter continuare.

## <a name="step-out"></a>Uscire dall'istruzione o dalla routine

Si supponga di aver completato l'esame del metodo `Draw` nella classe `Triangle` e di voler uscire dalla funzione rimanendo nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere **MAIUSC** + **F11** (oppure **Debug > Esci da istruzione/routine**).

     Questo comando riprende l'esecuzione dell'app e fa avanzare il debugger fino alla fine della funzione corrente.

     L'esecuzione dovrebbe tornare al ciclo `For Each` nel metodo `Main`. In caso contrario, premere **maiusc** + **F11** una seconda volta.

1. Fare clic sul margine sinistro per aggiungere un nuovo punto di interruzione nel ciclo `for`.

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

Fare clic sul pulsante **Riavvia** ![app riavvia](../../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti Debug (**CTRL** + **MAIUSC** + **F5**).

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente nel punto di interruzione impostato, nel metodo `shape.Draw()`.

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Mentre l'esecuzione è in pausa nel metodo `shape.Draw()`, passare il mouse sull'oggetto `shapes` per visualizzare il valore della proprietà predefinita, la proprietà `Count`.

1. Espandere l'oggetto `shapes` per visualizzarne tutte le proprietà, ad esempio il primo indice della matrice `[0]` con il valore di `Rectangle`.

     ![Visualizzare un suggerimento dati](../visual-basic/media/get-started-data-tip-vb.png "Visualizzare un suggerimento dati")

    È possibile espandere ulteriormente gli oggetti per visualizzarne le proprietà, ad esempio la proprietà `Height` del rettangolo.

    Spesso durante il debug è utile avere a disposizione un modo rapido per controllare i valori delle proprietà negli oggetti e i suggerimenti dati sono un ottimo strumento per eseguire questa operazione.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

     ![Esaminare le variabili nella finestra auto](../visual-basic/media/get-started-autos-window-vb.png "Finestra auto")

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. La finestra **Auto** mostra tutte le variabili usate nella riga corrente o nella riga precedente (vedere la documentazione per il comportamento specifico del linguaggio).

2. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione corrente.

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra principale dell'editor di codice fare clic con il pulsante destro del mouse sull'oggetto `shapes` e scegliere **Aggiungi espressione di controllo**.

    Viene visualizzata la finestra **Espressione di controllo** nella parte inferiore dell'editor di codice. È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

    Dopo aver impostato l'espressione di controllo nell'oggetto `shapes` è possibile visualizzare la modifica del valore durante gli spostamenti all'interno del debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** mostra sempre le variabili controllate (che appaiono disattivate quando sono fuori ambito).

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

1. Mentre l'esecuzione è in pausa nel ciclo `For Each`, fare clic sulla finestra **Stack di chiamate**, visualizzata per impostazione predefinita nel riquadro inferiore destro.

2. Fare clic su **F11** alcune volte fino a quando il debugger non viene messo in pausa nel metodo `MyBase.Draw` della classe `Rectangle` nell'editor del codice. Osservare la finestra **Stack di chiamate**.

    ![Esaminare lo stack di chiamate](../visual-basic/media/get-started-call-stack-vb.png "ExamineCallStack")

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `Rectangle.Draw` in questa app). La seconda riga indica che `Rectangle.Draw` è stato chiamato dalla funzione `Main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../../debugger/how-to-use-the-call-stack-window.md).

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Mentre il debugger è in pausa nella chiamata al metodo `MyBase.Draw` della classe `Rectangle`, usare il mouse per selezionare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla in alto di una riga alla chiamata al metodo `Console.WriteLine`.

1. Premere **F11**.

    Il debugger esegue nuovamente il metodo `Console.WriteLine` (nell'output della finestra della console verrà visualizzato l'output duplicato).

    Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Non è possibile ripristinare uno stato precedente dell'applicazione spostando il cursore.

1. Premere **F5** per continuare a eseguire l'app.

    L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../../debugger/debugger-feature-tour.md)
