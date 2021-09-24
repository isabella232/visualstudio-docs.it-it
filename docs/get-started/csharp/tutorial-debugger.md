---
title: 'Esercitazione: Eseguire il debug di codice C#'
description: Informazioni sulle funzionalità del debugger Visual Studio e su come avviare il debugger, esaminare il codice ed esaminare i dati in un'applicazione C#.
ms.custom: debug-experiment, vs-acquisition, get-started
ms.date: 09/14/2020
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22224b405f8e6cce41b99e36936bb2449f7827ea
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128374722"
---
# <a name="tutorial-learn-to-debug-c-code-using-visual-studio"></a>Esercitazione: Informazioni sul debug del codice C# tramite Visual Studio

Questo articolo descrive le funzionalità del debugger di Visual Studio con una procedura dettagliata. Per una panoramica di alto livello delle funzionalità del debugger, vedere [Presentazione del debugger](../../debugger/debugger-feature-tour.md). Quando si esegue il *debug dell'app* in genere si esegue l'applicazione con il debugger collegato. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile rivedere il codice ed esaminare i valori archiviati nelle variabili, impostare espressioni di controllo nelle variabili per rilevare le modifiche dei valori, esaminare il percorso di esecuzione del codice, verificare l'esecuzione di un ramo del codice e così via. Se è la prima volta che si prova a eseguire il debug del codice, è consigliabile leggere Debug per principianti assoluti [prima](../../debugger/debugging-absolute-beginners.md) di passare a questo articolo.

Sebbene l'app demo sia un'app C#, la maggior parte delle funzionalità è applicabile a C++, Visual Basic, F#, Python, JavaScript e altri linguaggi supportati da Visual Studio (F# non supporta la funzionalità Modifica e continuazione. F# e JavaScript non supportano la finestra **Auto**). Gli screenshot sono in linguaggio C#.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avvio del debugger e raggiungimento dei punti di interruzione
> * Uso dei comandi per esaminare il codice nel debugger
> * Ispezione delle variabili nelle finestre dei suggerimenti dati e del debugger
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2022"

È necessario aver installato Visual Studio 2022 Preview e il carico di lavoro **sviluppo desktop .NET.**

::: moniker-end

::: moniker range="vs-2019"

È necessario avere installato Visual Studio 2019 e il carico di lavoro **sviluppo multipiattaforma .NET Core.**

::: moniker-end

::: moniker range="vs-2017"

È necessario avere installato Visual Studio 2017 e il carico di lavoro **sviluppo multipiattaforma .NET Core.**

::: moniker-end

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="<=vs-2019"

Se è necessario installare il carico di lavoro ma è già Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro sviluppo multipiattaforma .NET Core,** quindi scegliere **Modifica**.

::: moniker-end

::: moniker range=">=vs-2022"

Se si dispone già di Visual Studio ma il carico di lavoro  **sviluppo desktop .NET** non è installato, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che avvia il Programma di installazione di Visual Studio. Nella finestra Programma di installazione di Visual Studio scegliere il carico di **lavoro Sviluppo desktop .NET,** quindi **scegliere Modifica**.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo, si creerà un progetto di applicazione console .NET Core. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

1. Nella barra dei menu superiore scegliere **File** > **nuovo** > **Project**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **C#** e quindi scegliere **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al progetto il *nome get-started-debugging*.

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato il linguaggio e i filtri della piattaforma, scegliere il modello **App console** per .NET Core e quindi **scegliere Avanti.**

   ![Screenshot del modello C# per l'app console.](../csharp/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Se il modello App **console** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *GetStartedDebugging* nella casella Project **nome.** Scegliere quindi **Avanti**.

1. Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi **scegliere Crea**.

   Visual Studio aprirà il nuovo progetto.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Scegliere quindi **C#** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato i filtri della lingua e della piattaforma, scegliere il modello **Applicazione console** e quindi **scegliere Avanti.**

   :::image type="content" source="media/vs-2022/get-started-create-console-project.png" alt-text="Screenshot del modello &quot;Applicazione console&quot; nella finestra &quot;Crea un nuovo progetto&quot; di Visual Studio 2022.":::

   > [!NOTE]
   > Se il modello Applicazione **console** non è visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Nella finestra di dialogo Programma di installazione di Visual Studio quindi scegliere il carico di **lavoro Sviluppo desktop .NET.**

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *GetStartedDebugging* nella casella Project **nome.** Scegliere quindi **Avanti**.

1. Nella finestra **Informazioni aggiuntive** verificare che **.NET 6.0 (anteprima)** sia selezionato nel menu a discesa **Framework** e quindi scegliere **Crea**.

    Visual Studio aprirà il nuovo progetto.

::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

In *Program.cs* sostituire tutto il codice predefinito con il codice seguente:

```csharp
using System;

class ArrayExample
{
    static void Main()
    {
        char[] letters = { 'f', 'r', 'e', 'd', ' ', 's', 'm', 'i', 't', 'h'};
        string name = "";
        int[] a = new int[10];
        for (int i = 0; i < letters.Length; i++)
        {
            name += letters[i];
            a[i] = i + 1;
            SendMessage(name, a[i]);
        }
        Console.ReadKey();
    }

    static void SendMessage(string name, int msg)
    {
        Console.WriteLine("Hello, " + name + "! Count to " + msg);
    }
}
```

## <a name="start-the-debugger"></a>Avviare il debugger.

::: moniker range="<=vs-2019"

1. Premere **F5** (**Debug > Avvia** debug  ) o il pulsante Avvia debug Immagine del ![pulsante "Avvia debug".](../../debugger/media/dbg-tour-start-debugging.png "Avvia debug") nella barra degli strumenti Debug.

     **F5** avvia l'app con il debugger collegato al processo dell'app. Fino ad ora, tuttavia, non è stata eseguita alcuna operazione per esaminare il codice. L'app viene quindi caricata e verrà visualizzato l'output della console.

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

1. Arrestare il debugger premendo l'immagine di arresto ![rossa del pulsante "Arresta debug".](../../debugger/media/dbg-tour-stop-debugging.png "Debug") pulsante (**MAIUSC**  +  **F5**).

1. Nella finestra della console premere un tasto per chiudere la finestra della console.

::: moniker-end

::: moniker range=">=vs-2022"

In questo caso si usano principalmente i tasti di scelta rapida, perché è un modo rapido per eseguire i comandi del debugger. Vengono anche notati comandi equivalenti, ad esempio i comandi della barra degli strumenti o dei menu.

1. Per avviare il debugger, selezionare **F5** oppure scegliere il pulsante Debug  destinazione sulla barra degli strumenti Standard oppure scegliere il pulsante Avvia debug sulla barra degli strumenti Debug oppure scegliere **Debug** Avvia debug dalla barra dei  >  menu.

    :::image type="content" source="media/vs-2022/dbg-tour-start-debugging.png" alt-text="Screenshot del pulsante &quot;Debug Target&quot; sulla barra degli strumenti Standard di Visual Studio 2022.":::

    **F5** avvia l'app con il debugger collegato al processo dell'app. Poiché non è stato fatto nulla di speciale per esaminare il codice, l'app viene eseguita fino al completamento e viene visualizzato l'output della console.

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

1. Per arrestare il debugger, selezionare **MAIUSC+F5** oppure scegliere il pulsante Arresta debug sulla barra degli strumenti Debug oppure scegliere **Debug** Interrompi debug dalla barra dei  >  menu.

    :::image type="content" source="media/vs-2022/dbg-tour-stop-debugging.png" alt-text="Screenshot del pulsante &quot;Arresta debug&quot; sulla barra degli strumenti Debug di Visual Studio 2022.":::

1. Nella finestra della console selezionare un tasto qualsiasi per chiudere la finestra della console.

::: moniker-end

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

::: moniker range="<=vs-2019"

1. Nel ciclo `for` della funzione `Main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `name += letters[i];`

    Cerchio rosso ![Immagine di un punto di interruzione.](../../debugger/media/dbg-breakpoint.png "Punto di interruzione") viene visualizzato nel punto in cui si imposta il punto di interruzione.

    I punti di interruzione sono una delle funzionalità di base ed essenziali del debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Premere **F5 o** il pulsante Avvia **debug** Screenshot del pulsante "Avvia ![debug".](../../debugger/media/dbg-tour-start-debugging.png "Avvia debug")L'app viene avviata e il debugger viene eseguito sulla riga di codice in cui si imposta il punto di interruzione.

    ![Impostare e raggiungere un punto di interruzione](../csharp/media/get-started-set-breakpoint.gif)

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

     Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio. Per informazioni sui diversi tipi di punti di interruzione che è possibile impostare, ad esempio i punti di interruzione condizionali, vedere [Uso dei punti di interruzione](../../debugger/using-breakpoints.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. Nel ciclo `for` della funzione `Main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `name += letters[i];`

    Quando viene impostato il punto di interruzione viene visualizzato un cerchio rosso.

    :::image type="content" source="media/vs-2022/dbg-tour-breakpoint.png" alt-text="Screenshot di un punto di interruzione in Visual Studio 2022."::: 

    I punti di interruzione sono una funzionalità essenziale del debug affidabile. È possibile impostare punti di interruzione nel punto in cui si vuole che Visual Studio sospende il codice in esecuzione in modo da esaminare i valori delle variabili o il comportamento della memoria o sapere se viene eseguito o meno un ramo di codice.

1. Per avviare il debug, premere  **F5** oppure scegliere il pulsante  Destinazione di debug sulla barra degli strumenti Standard oppure scegliere il pulsante Avvia debug sulla barra degli strumenti Debug oppure scegliere **Debug** Avvia debug dalla barra  >   dei menu. L'app viene avviata e il debugger viene eseguito fino alla riga di codice in cui è stato impostato il punto di interruzione.

    :::image type="content" source="media/vs-2022/get-started-set-breakpoint.png" alt-text="Screenshot che mostra un punto di interruzione nell'editor di codice Visual Studio 2022, con l'esecuzione del codice sospesa in corrispondenza del punto di interruzione.":::

    La freccia gialla punta all'istruzione in cui è stato sospeso il debugger. L'esecuzione dell'app viene sospesa nello stesso punto, con l'istruzione non ancora eseguita.

    Quando l'app non è in esecuzione, **F5** avvia il debugger, che eseguirà l'app fino a raggiungere il primo punto di interruzione. Se l'app viene sospesa in corrispondenza di un punto di interruzione, **F5** continuerà a eseguire l'app fino a raggiungere il punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce in dettaglio la riga o la sezione di codice che si vuole esaminare. Per altre informazioni sui diversi tipi di punti di interruzione che è possibile impostare, ad esempio i punti di interruzione condizionali, vedere [Uso dei punti di interruzione.](../../debugger/using-breakpoints.md)

::: moniker-end

## <a name="navigate-code-and-inspect-data-by-using-data-tips"></a>Esplorare il codice ed esaminare i dati usando suggerimenti dati

::: moniker range="<=vs-2019"

In questa esercitazione nella maggior parte dei casi vengono usati tasti di scelta rapida che rappresentano un modo rapido per eseguire l'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono indicati tra parentesi).

1. Mentre è in pausa nell'istruzione, passare il puntatore sulla variabile per visualizzare il valore predefinito, il valore del primo `name += letters[i]` `letters` elemento nella matrice, `char[10]` .

     Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Espandere la `letters` variabile per visualizzarne le proprietà, che includono tutti gli elementi contenuti nella variabile.

     ![Screenshot del debugger sospeso in corrispondenza dell'istruzione 'name+= letters[I]'.](../csharp/media/get-started-view-data-tip.png)

1. Passare quindi il puntatore `name` sulla variabile per visualizzarne il valore corrente, una stringa vuota.

1. Premere **F10** (o scegliere **Debug >** Esegui istruzione/comando ) due volte per passare alla chiamata al metodo e quindi premere `SendMessage` **F10** ancora una volta.

     F10 fa avanzare il debugger all'istruzione successiva senza eseguire istruzioni in funzioni o metodi nel codice dell'app (il codice viene comunque eseguito). Premendo F10 nella chiamata al metodo, è stato ignorato il codice di implementazione per (che potrebbe non essere interessato al `SendMessage` `SendMessage` momento).

1. Premere **F10** (o **Esegui** debug istruzione/istruzione ) alcune volte per eseguire l'iterazione più volte nel ciclo, sospendere di nuovo in corrispondenza del punto di interruzione e passare ogni volta il puntatore del mouse sulla variabile per controllarne il >  `for` `name` valore.

     ![Screenshot animato del debugger Visual Studio che mostra l'effetto della pressione di F10 per eseguire l'istruzione/esecuzione ed eseguire l'iterazione di un ciclo durante il debug.](../csharp/media/get-started-data-tip.gif)

     Il valore della variabile cambia a ogni iterazione del ciclo, visualizzando i valori `for` di , quindi , e così `f` `fr` `fre` via. Per far avanzare il debugger attraverso il ciclo più velocemente in questo scenario, è possibile premere **F5** (o scegliere **Debug** continua) invece di passare al punto di interruzione anziché  >  all'istruzione successiva.

     Spesso, durante il debug, è necessario controllare rapidamente i valori delle proprietà sulle variabili, per vedere se si stanno archiviando i valori previsti, e i suggerimenti dati costituiscono un valido strumento per questa operazione.

1. Mentre è ancora in pausa nel ciclo nel metodo , premere `for` `Main` **F11** (o scegliere Debug > Esegui istruzione ) fino a quando non si sospende la chiamata `SendMessage` al metodo.

     Si dovrebbe essere in questa riga di codice:

     `SendMessage(name, a[i]);`

1. Premere **F11** ancora una volta per eseguire un'istruzione nel `SendMessage` metodo .

     Il puntatore giallo avanza nel `SendMessage` metodo .

     ![Screenshot del puntatore di esecuzione nel metodo 'SendMessage'.](../csharp/media/get-started-f11.png "F10 Step Into")

     F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. Per impostazione predefinita, il debugger ignora il codice non utente (per informazioni dettagliate, vedere [Just My Code](../../debugger/just-my-code.md)).

     Si immagini di aver esaminato il metodo e di voler uscire dal metodo ma rimanere `SendMessage` nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere  + **MAIUSC+F11** (o **Esegui debug > esci da istruzione/uscita**).

     Questo comando riprende l'esecuzione dell'app (e fa avanzare il debugger) fino alla fine del metodo o della funzione corrente.

     Si dovrebbe tornare al `for` ciclo nel metodo , sospeso in corrispondenza della chiamata al metodo `Main` `SendMessage` . Per altre informazioni sui diversi modi per spostarsi nel codice, vedere [Esplorare il codice nel debugger.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

::: moniker range=">=vs-2022"

1. Mentre è in pausa nell'istruzione , passare il mouse sulla variabile per visualizzare un suggerimento dati che mostra le dimensioni della matrice `name += letters[i]` e il tipo di `letters` elemento, `char[10]` .

    > [!NOTE]
    > Una delle funzionalità più utili del debugger è la possibilità di esaminare una variabile. Spesso, quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili hanno valori previsti in un determinato momento. La visualizzazione dei suggerimenti dati è un buon metodo per verifica ciò.

1. Espandere la `letters` variabile per visualizzare tutti gli elementi della matrice e i relativi valori.

    :::image type="content" source="media/vs-2022/get-started-view-data-tip.png" alt-text="Screenshot di un suggerimento dati del debugger in Visual Studio 2022 che mostra i valori degli elementi per la variabile di matrice 'letters'.":::

1. Passare il mouse `name` sulla variabile per visualizzarne il valore corrente, ovvero una stringa vuota.

1. Per far avanzare il debugger all'istruzione successiva,  premere **F10** oppure scegliere il pulsante Esegui istruzione/istruzione/istruzione sulla barra degli strumenti Debug oppure scegliere **Esegui** debug istruzione/istruzione/istruzione  >   dalla barra dei menu. Premere **F10 due** volte per passare oltre la chiamata `SendMessage` al metodo. 

    **F10 fa** avanzare il debugger senza eseguire un'istruzione alla funzione o ai metodi, anche se il codice è ancora in esecuzione. In questo modo, è stato ignorato il debug del codice nel metodo , a cui non si è `SendMessage` interessati al momento.

1. Per scorrere il ciclo `for` più volte, premere **ripetutamente F10.** Durante ogni iterazione del ciclo, sospendere in corrispondenza del punto di interruzione e quindi passare il mouse sulla `name` variabile per controllarne il valore nel suggerimento dati.

    :::image type="content" source="media/vs-2022/get-started-data-tip.png" alt-text="Screenshot di un suggerimento dati del debugger in Visual Studio 2022 che mostra il valore stringa per la variabile 'name'.":::

    Il valore della variabile cambia a ogni iterazione del ciclo, visualizzando i valori `for` di , quindi , e così `f` `fr` `fre` via. Per far avanzare il debugger nel ciclo più velocemente, premere **F5,** che consente di passare al punto di interruzione anziché all'istruzione successiva.

1. Mentre è in pausa nel ciclo del metodo, premere `for` `Main` **F11**   oppure scegliere il >  pulsante Esegui istruzione dalla barra degli strumenti Debug oppure scegliere Esegui debug istruzione dalla barra dei menu fino a raggiungere la chiamata al `SendMessage` metodo.

     Il debugger deve essere sospeso in corrispondenza di questa riga di codice:

     `SendMessage(name, a[i]);`

1. Per eseguire `SendMessage` un'istruzione nel metodo, premere **di nuovo F11.**

     Il puntatore giallo avanza nel `SendMessage` metodo .

     :::image type="content" source="media/vs-2022/get-started-f11.png" alt-text="Screenshot che mostra il puntatore di esecuzione del debugger all'interno del metodo 'SendMessage'.":::

     **F11** consente di esaminare il flusso di esecuzione del codice in modo più approfondito. Per eseguire un'istruzione in un metodo da una chiamata al metodo, **premere F11.** Per impostazione predefinita, il debugger ignora l'esecuzione di istruzioni in metodi non utente. Per informazioni sul debug di codice non utente, [vedere Just My Code](../../debugger/just-my-code.md).

     Dopo aver completato il debug del metodo, si è pronti per tornare `SendMessage` al ciclo del metodo `for` `main` .

1. Per uscire dal metodo, premere `SendMessage` **MAIUSC+F11**  oppure scegliere il pulsante  Uscita dalla barra degli strumenti Debug oppure scegliere Esegui debug istruzione/uscita >  dalla barra dei menu.

     **Esce dall'istruzione/uscita** riprende l'esecuzione dell'app e fa avanzare il debugger fino a quando il metodo o la funzione corrente non viene restituita.

     Verrà visualizzato il puntatore giallo nel ciclo del metodo, sospeso `for` alla chiamata al `Main` `SendMessage` metodo. Per altre informazioni sui diversi modi per spostarsi nel codice, vedere [Esplorare il codice nel debugger.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con il pulsante per l'esecuzione fino alla riga selezionata dall'utente

::: moniker range="<=vs-2019"

1. Premere **F5 per** passare di nuovo al punto di interruzione.

1. Nell'editor di codice scorrere verso il basso e passare il puntatore del mouse sul metodo nel metodo fino al pulsante verde Esegui fino al clic Immagine del pulsante "Esegui fino al `Console.WriteLine` `SendMessage` ![clic".](../../debugger/media/dbg-tour-run-to-click.png "RunToClick")  a sinistra. La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

     ![Screenshot del pulsante "Esegui fino al clic".](../csharp/media/get-started-run-to-click.png "Esegui fino alla riga selezionata")

   > [!NOTE]
   > Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è una nuova funzionalità di [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Se il pulsante freccia verde non è visualizzato, usare **F11** in questo esempio per far avanzare il debugger nella posizione giusta.

1. Fare clic **sul pulsante Esegui fino alla** selezione Immagine del pulsante !["Esegui fino a fare clic".](../../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Il debugger passa al `Console.WriteLine` metodo .

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **F5 per** passare di nuovo al punto di interruzione.

1. Nell'editor di codice passare il puntatore del mouse sulla chiamata al metodo nel metodo fino a quando non viene visualizzato il pulsante Esegui fino al clic `Console.WriteLine` `SendMessage` a sinistra.  La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

    :::image type="content" source="media/vs-2022/get-started-run-to-click.png" alt-text="Screenshot che mostra il pulsante &quot;Esegui fino al clic&quot; Visual Studio 2022.":::

1. Scegliere il **pulsante Esegui fino a** clic. In alternativa, con il cursore in `Console.WriteLine` corrispondenza dell'istruzione selezionare **CTRL+F10.** In caso contrario, fare clic con il pulsante destro del mouse sulla chiamata al metodo e scegliere `Console.WriteLine` **Esegui fino al cursore** dal menu di scelta rapida.

    Il debugger passa alla chiamata `Console.WriteLine` al metodo .

    **L'uso del pulsante Esegui** fino alla selezione è simile all'impostazione di un punto di interruzione temporaneo ed è utile per spostarsi rapidamente all'interno di un'area visibile del codice dell'app in un file aperto.

::: moniker-end

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

::: moniker range="<=vs-2019"

Fare clic **sul pulsante Restart** ![Image (Riavvia immagine) del pulsante "Restart App" (Riavvia app).](../../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti Debug (**CTRL**  +  **MAIUSC**  +  **F5**).

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente in corrispondenza del punto di interruzione impostato in precedenza all'interno del `for` ciclo.

::: moniker-end

::: moniker range=">=vs-2022"

Per rieseguire l'app dall'inizio nel debugger, selezionare **CTRL+MAIUSC+F5** oppure scegliere il pulsante Riavvia sulla barra degli strumenti Debug oppure scegliere **Riavvia** debug dalla barra dei  >  menu.

:::image type="content" source="media/vs-2022/dbg-tour-restart-debugging.png" alt-text="Screenshot del pulsante &quot;Riavvia&quot; nella barra degli strumenti Debug di Visual Studio 2022.":::

**Riavvia** arresta il debugger e lo riavvia in un unico passaggio. Quando il debugger viene riavviato, verrà eseguito fino al primo punto di interruzione, ovvero il punto di interruzione impostato in precedenza all'interno del `for` ciclo e quindi sospeso.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

::: moniker range="<=vs-2019"

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

    Se è chiuso, aprirlo mentre è in  pausa nel debugger scegliendo > **Debug Windows** > **auto.**

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. La finestra **Auto** mostra tutte le variabili usate nella riga corrente o nella riga precedente (vedere la documentazione per il comportamento specifico del linguaggio).

1. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

1. Espandere la `letters` variabile per visualizzare gli elementi in essa contenuti.

     ![Screenshot della finestra Variabili locali in Visual Studio.](../csharp/media/get-started-locals-window.png "finestra Variabili locali")

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione corrente.

::: moniker-end

::: moniker range=">=vs-2022"

Le **finestre Auto e** Variabili **locali** mostrano i valori delle variabili durante il debug. Le finestre sono disponibili solo durante una sessione di debug. La **finestra Auto mostra** le variabili usate nella riga corrente in cui si trova il debugger e la riga precedente. La **finestra Variabili** locali mostra le variabili definite nell'ambito locale, che in genere è la funzione o il metodo corrente.

1. Mentre il debugger è sospeso, visualizzare la **finestra Auto nella** parte inferiore dell'editor di codice.

    Se la **finestra Auto è** chiusa, selezionare **CTRL+D, A** o scegliere Debug Windows  >  > **auto dalla** barra dei menu.

1. Con il debugger ancora sospeso, visualizzare la **finestra** Variabili locali in una scheda accanto **alla finestra Auto.**

    Se la **finestra Variabili** locali è chiusa, selezionare  **CTRL+D, L** o scegliere > **Debug Windows** variabili > **locali**.

1. Nella finestra **Variabili locali** espandere la variabile per visualizzare gli elementi della matrice e i `letters` relativi valori.

     :::image type="content" source="media/vs-2022/get-started-locals-window.png" alt-text="Screenshot della finestra Variabili locali in Visual Studio 2022, con la variabile di matrice &quot;letters&quot; espansa.":::

Per altre informazioni **sulle finestre Auto e** **Variabili** locali, vedere Esaminare le variabili nelle finestre Auto e [Variabili locali](/visualstudio/debugger/autos-and-locals-windows?view=vs-2022&preserve-view=true).

::: moniker-end

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

::: moniker range="<=vs-2019"

1. Nella finestra principale dell'editor di codice fare clic con il pulsante destro del mouse sulla `name` variabile e scegliere Aggiungi espressioni di **controllo**.

    Viene visualizzata la finestra **Espressione di controllo** nella parte inferiore dell'editor di codice. È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

    A questo punto, è disponibile un controllo impostato sulla variabile ed è possibile visualizzarne la modifica del `name` valore durante lo spostamento nel debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** mostra sempre le variabili controllate (che appaiono disattivate quando sono fuori ambito).

::: moniker-end

::: moniker range=">=vs-2022"

È possibile specificare una variabile o un'espressione che si vuole tenere d'occhio durante l'esecuzione del codice aggiungendola &mdash; alla finestra Espressione **di** controllo.

1. Mentre il debugger è sospeso, fare clic con il pulsante destro del mouse sulla `name` variabile e scegliere Aggiungi espressioni di **controllo**.

    La **finestra Espressioni** di controllo viene aperta per impostazione predefinita nella parte inferiore dell'editor di codice.

1. Ora che è stato impostato un controllo sulla variabile, eseguire il codice un'istruzione alla volta per visualizzare il valore della modifica della variabile `name` `name` con ogni `for` iterazione del ciclo. 

    A differenza delle altre  finestre delle variabili, la finestra Espressioni di controllo mostra sempre le variabili che si stanno osservando, anche se saranno disattivate quando non sono nell'ambito.

Per altre informazioni sulla **finestra Espressioni di** controllo, vedere Variabili watch con le finestre Espressioni di [controllo](/visualstudio/debugger/watch-and-quickwatch-windows?view=vs-2022&preserve-view=true).

::: moniker-end

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

::: moniker range="<=vs-2019"

1. Mentre l'esecuzione è in pausa nel ciclo `for`, fare clic sulla finestra **Stack di chiamate**, visualizzata per impostazione predefinita nel riquadro inferiore destro.

    Se è chiuso, aprirlo durante la sospensione  nel debugger scegliendo Debug Windows >  > **Stack di chiamate**.

1. Fare **clic su F11** alcune volte fino a quando il debugger non viene sospeso nel `SendMessage` metodo . Osservare la finestra **Stack di chiamate**.

    ![Screenshot della finestra Stack di chiamate in Visual Studio.](../csharp/media/get-started-call-stack.png "ExamineCallStack")

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `SendMessage` in questa app). La seconda riga indica che `SendMessage` è stato chiamato dal metodo `Main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

::: moniker range=">=vs-2022"

Lo **stack di chiamate** consente di comprendere il flusso di esecuzione dell'app, visualizzando l'ordine in cui vengono chiamati metodi e funzioni.

1. Mentre il debugger è sospeso nel ciclo, visualizzare la finestra Stack di chiamate, che si apre per impostazione predefinita nel riquadro `for` inferiore destro dell'editor  di codice.

    Se la **finestra Stack di** chiamate è chiusa,  selezionare **CTRL+D, C** o scegliere Debug Windows >  > **Stack di chiamate** dalla barra dei menu.

    Nella finestra **Stack di** chiamate verrà visualizzato il puntatore giallo in corrispondenza del metodo `Main` corrente.

1. Selezionare **F11** alcune volte finché il debugger non viene sospeso nel `SendMessage` metodo .

    La riga superiore della finestra **Stack di chiamate** mostra la funzione corrente, ovvero il metodo `SendMessage` . La seconda riga indica che il `SendMessage` metodo è stato chiamato dal metodo `Main` .

    :::image type="content" source="media/vs-2022/get-started-call-stack.png" alt-text="Screenshot della finestra Stack di chiamate in Visual Studio 2022.":::

   > [!NOTE]
   > La **finestra Stack di** chiamate è simile alla prospettiva Debug in alcuni ID, ad esempio Eclipse.

    Nella finestra **Stack di** chiamate è possibile fare doppio clic su una riga di codice per passare a tale codice sorgente, che modifica l'ambito corrente esaminato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire punti di interruzione nelle funzioni specificate, far avanzare il debugger usando Esegui fino al **cursore** o passare al codice sorgente. 

Per altre informazioni sullo **stack di chiamate,** [vedere Procedura: Esaminare lo stack di chiamate](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

::: moniker range="<=vs-2019"

1. Premere **F11** due volte per eseguire il `Console.WriteLine` metodo .

1. Con il debugger sospeso nella chiamata al metodo , usare il mouse per afferrare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla verso l'alto di una riga, di nuovo `SendMessage` su `Console.WriteLine` .

1. Premere **F11.**

    Il debugger esegue nuovamente il metodo `Console.WriteLine` (visualizzato nell'output della finestra della console).

    Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Non è possibile ripristinare uno stato precedente dell'applicazione spostando il cursore.

1. Premere **F5** per continuare a eseguire l'app.

    L'esercitazione è stata completata.

::: moniker-end

::: moniker range=">=vs-2022"

È possibile spostare il puntatore di esecuzione per modificare il flusso dell'app durante il debug.

1. Con il debugger sospeso alla chiamata al metodo nel ciclo, selezionare F11 tre volte per eseguire un'istruzione nel metodo e per passare oltre il metodo dopo `SendMessage` `for`  `SendMessage` `Console.WriteLine` l'esecuzione.

    Il debugger viene ora sospeso alla parentesi graffa di chiusura finale del `SendMessage` metodo .

1. Usare il mouse per afferrare la freccia gialla o il puntatore di esecuzione (nel margine sinistro) e quindi trascinare il puntatore di una riga verso l'alto.

    Il debugger è ora di nuovo `Console.WriteLine` sull'istruzione .

1. Selezionare **F11.**

    Il debugger esegue nuovamente il metodo e nell'output della finestra della console verrà visualizzata una riga `Console.WriteLine` duplicata.

1. Selezionare **F5 per** continuare a eseguire l'app.

Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

> [!WARNING]
> Usare questa funzionalità con cautela. Nella descrizione comando del puntatore di esecuzione verrà visualizzato un avviso relativo alla possibilità di conseguenze impreviste. Potrebbero essere visualizzati anche altri avvisi. Lo spostamento del puntatore di esecuzione non può ripristinare lo stato precedente dell'applicazione.

Per altre informazioni sulla modifica del flusso di esecuzione, vedere [Spostare il puntatore per modificare il flusso di esecuzione.](/visualstudio/debugger/navigating-through-code-with-the-debugger?view=vs-2022#BKMK_Set_the_next_statement_to_execute&preserve-view=true)

L'esercitazione è stata completata.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. È possibile ottenere un'occhiata di alto livello alle funzionalità del debugger insieme ai collegamenti ad altre informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../../debugger/debugger-feature-tour.md)
