---
title: 'Esercitazione: Eseguire il debug Visual Basic codice'
description: Informazioni sulle funzionalità del debugger Visual Studio e su come avviare il debugger, eseguire il codice un'istruzione alla pagina ed esaminare i dati in un Visual Basic appalto.
ms.custom: debug-experiment, vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- VB
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cf02a169d775c2fb8391ee3c700f726c7462c660
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429571"
---
# <a name="tutorial-learn-to-debug-visual-basic-code-using-visual-studio"></a>Esercitazione: Informazioni sul debug del codice Visual Basic tramite Visual Studio

Questo articolo descrive le funzionalità del debugger di Visual Studio con una procedura dettagliata. Per una panoramica di alto livello delle funzionalità del debugger, vedere [Presentazione del debugger](../../debugger/debugger-feature-tour.md). Quando si esegue il *debug dell'app* in genere si esegue l'applicazione con il debugger collegato. Durante il debug, il debugger offre diversi modi per vedere le operazioni eseguite dal codice durante l'esecuzione. È possibile rivedere il codice ed esaminare i valori archiviati nelle variabili, impostare espressioni di controllo nelle variabili per rilevare le modifiche dei valori, esaminare il percorso di esecuzione del codice, verificare l'esecuzione di un ramo del codice e così via. Se è la prima volta che si esegue il debug del codice, può essere utile leggere [Debug per principianti](../../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

Anche se l'app demo è Visual Basic, la maggior parte delle funzionalità è applicabile a C#, C++, F#, Python, JavaScript e altri linguaggi supportati da Visual Studio (F# non supporta Modifica e continuazione. F# e JavaScript non supportano la finestra **Auto**). Gli screenshot sono in Visual Basic.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Avvio del debugger e raggiungimento dei punti di interruzione
> * Uso dei comandi per esaminare il codice nel debugger
> * Ispezione delle variabili nelle finestre dei suggerimenti dati e del debugger
> * Esaminare lo stack di chiamate

## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

È necessario avere installato Visual Studio 2019 e il carico di lavoro **sviluppo multipiattaforma .NET Core.**

::: moniker-end
::: moniker range="vs-2017"

È necessario avere installato Visual Studio 2017 e il carico di lavoro **sviluppo multipiattaforma .NET Core.**

::: moniker-end

::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

Se è necessario installare il carico di lavoro ma è già Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro sviluppo multipiattaforma .NET Core,** quindi scegliere **Modifica**.

::: moniker-end

::: moniker range=">=vs-2022"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

Se è necessario installare il carico di lavoro ma è già Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET**, quindi scegliere **Modifica**.

::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

In primo luogo, si creerà un progetto di applicazione console .NET Core. Il tipo di progetto include fin dall'inizio tutti i file modello necessari.

::: moniker range="vs-2017"

1. Aprire Visual Studio 2017.

2. Nella barra dei menu superiore scegliere **File** > **nuovo** > **Project**.

3. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **Visual Basic**, quindi selezionare **.NET Core**. Nel riquadro centrale scegliere **Console App (.NET Core)** (App console (.NET Core)). Assegnare quindi al progetto il *nome get-started-debugging*.

     Se non viene visualizzato il modello di progetto **Applicazione console (.NET Core)**, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro a sinistra della finestra di dialogo **Nuovo progetto**.

     Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo multipiattaforma .NET Core**, quindi scegliere **Modifica**.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato il linguaggio e i filtri della piattaforma, scegliere il modello **App console** per .NET Core e quindi **scegliere Avanti.**

   ![Screenshot che mostra la finestra Crea un nuovo progetto con "console" nella casella di ricerca e "Visual Basic" e "Windows" selezionati per i filtri Lingua e Piattaforma. Il modello di progetto Applicazione console è selezionato.](../visual-basic/media/vs-2019/get-started-create-console-project.png)

   > [!NOTE]
   > Se il modello App **console** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Scegliere quindi il carico di lavoro **Sviluppo multipiattaforma .NET Core** nel programma di installazione di Visual Studio.

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *get-started-debugging* nella casella Project **nome.** Scegliere quindi **Avanti**.

1. Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi **scegliere Crea**.

   Visual Studio aprirà il nuovo progetto.
   
::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio.

   Se la finestra iniziale non è aperta, scegliere **Finestra** > **iniziale file**.

1. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

1. Nella finestra **Crea un nuovo progetto** immettere o digitare *console* nella casella di ricerca. Quindi scegliere **Visual Basic** dall'elenco Linguaggio e **Windows** dall'elenco Piattaforma. 

   Dopo aver applicato il linguaggio e i filtri della piattaforma, scegliere il modello **Applicazione console** per .NET Core e quindi **scegliere Avanti.**

   :::image type="content" source="media/vs-2022/get-started-create-console-project.png" alt-text="Screenshot che mostra la finestra Crea un nuovo progetto con &quot;console&quot; nella casella di ricerca e &quot;Visual Basic&quot; e &quot;Windows&quot; selezionati per i filtri Lingua e Piattaforma. Il modello di progetto Applicazione console è selezionato.":::

   > [!NOTE]
   > Se il modello Applicazione **console** non viene visualizzato, è possibile installarlo dalla finestra **Crea un nuovo** progetto. Nel messaggio **L'elemento cercato non è stato trovato?** scegliere il collegamento **Installa altri strumenti e funzionalità**. Nella finestra di dialogo Programma di installazione di Visual Studio quindi scegliere il carico di **lavoro Sviluppo desktop .NET.**

1. Nella finestra **Configura il nuovo progetto** digitare o immettere *get-started-debugging* nella casella Project **nome.** Scegliere quindi **Avanti**.

1. Nella finestra **Informazioni aggiuntive** verificare che il framework di destinazione consigliato sia (.NET 6.0) e quindi scegliere **Crea**.

   Visual Studio aprirà il nuovo progetto.
   
::: moniker-end

## <a name="create-the-application"></a>Creare l'applicazione

1. In *Program.vb* sostituire tutto il codice predefinito con il codice seguente:

    ```vb
    Imports System

    Class ArrayExample
        Public Shared Sub Main()
            Dim letters As Char() = {"f"c, "r"c, "e"c, "d"c, " "c, "s"c, "m"c, "i"c, "t"c, "h"c}
            Dim name As String = ""
            Dim a As Integer() = New Integer(9) {}

            For i As Integer = 0 To letters.Length - 1
                name += letters(i)
                a(i) = i + 1
                SendMessage(name, a(i))
            Next

            Console.ReadKey()
        End Sub

        Private Shared Sub SendMessage(ByVal name As String, ByVal msg As Integer)
            Console.WriteLine("Hello, " & name & "! Count to " & msg)
        End Sub
    End Class
    ```

## <a name="start-the-debugger"></a>Avviare il debugger.

::: moniker range="<=vs-2019"

1. Premere **F5** (**Debug > Avvia** debug ) o il **pulsante** Avvia debug sulla barra degli :::image type="icon" source="../../debugger/media/dbg-tour-start-debugging.png"::: strumenti debug.

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

2. Arrestare il debugger premendo il pulsante di arresto :::image type="icon" source="../../debugger/media/dbg-tour-stop-debugging.png"::: rosso (**MAIUSC** + **F5**).

3. Nella finestra della console premere un tasto per chiudere la finestra della console.

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **F5** (**Debug > Avvia** debug ) o selezionare il pulsante verde **Avvia** debug nella barra degli strumenti debug.

    :::image type="content" source="media/vs-2022/debug-toolbar-start-button.png" alt-text="Screenshot che mostra la barra degli strumenti debug con il pulsante verde &quot;Avvia debug&quot; evidenziato.":::

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

2. Arrestare il debugger premendo (**MAIUSC** F5 ) o selezionare il pulsante rosso +  **Arresta** debug sulla barra degli strumenti debug.

    :::image type="content" source="media/vs-2022/debug-toolbar-stop-button.png" alt-text="Screenshot che mostra la barra degli strumenti Debug con il pulsante rosso &quot;Arresta debug&quot; evidenziato.":::

3. Nella finestra della console premere un tasto per chiudere la finestra della console.

::: moniker-end
## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

::: moniker range="<=vs-2019"

1. Nel ciclo `For` della funzione `Main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `name += letters(i)`

    Viene visualizzato un cerchio :::image type="icon" source="../../debugger/media/dbg-breakpoint.png"::: rosso in cui è stato impostato il punto di interruzione.

    I punti di interruzione sono una delle funzionalità di base ed essenziali del debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

2. Premere **F5 o** il **pulsante Avvia** debug , l'app viene avviata e il debugger viene eseguito sulla riga di codice in cui si imposta il punto :::image type="icon" source="../../debugger/media/dbg-tour-start-debugging.png"::: di interruzione.

    ![Screenshot che mostra la finestra Visual Studio dell'editor di codice con l'esecuzione arrestata in corrispondenza di un punto di interruzione.](../visual-basic/media/get-started-hit-breakpoint-vb.png)

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

     Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio. Per informazioni sui diversi tipi di punti di interruzione che è possibile impostare, ad esempio i punti di interruzione condizionali, vedere [Uso dei punti di interruzione](../../debugger/using-breakpoints.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. Nel ciclo `For` della funzione `Main` impostare un punto di interruzione facendo clic sul margine sinistro della riga di codice seguente:

    `name += letters(i)`

    Quando viene impostato il punto di interruzione viene visualizzato un cerchio rosso.

    I punti di interruzione sono una delle funzionalità di base ed essenziali del debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

2. Premere **F5** (**Debug >** Avvia debug  ) o il pulsante Avvia debug sulla barra degli strumenti debug, l'app viene avviata e il debugger viene eseguito fino alla riga di codice in cui è stato impostato il punto di interruzione.

    :::image type="content" source="media/vs-2022/get-started-hit-breakpoint-vb.png" alt-text="Screenshot che mostra la finestra Visual Studio dell'editor di codice con l'esecuzione arrestata in corrispondenza di un punto di interruzione.":::

    La freccia gialla rappresenta l'istruzione in corrispondenza della quale il debugger si è interrotto e il punto in cui anche l'esecuzione dell'app viene sospesa (l'istruzione non è ancora stata eseguita).

    Se l'app non è ancora in esecuzione, **F5** avvia il debugger e lo arresta in corrispondenza del primo punto di interruzione. In caso contrario, **F5** continua l'esecuzione dell'app fino al punto di interruzione successivo.

    I punti di interruzione sono una funzionalità utile quando si conosce la riga di codice o la sezione di codice che si vuole esaminare nel dettaglio. Per informazioni sui diversi tipi di punti di interruzione che è possibile impostare, ad esempio i punti di interruzione condizionali, vedere [Uso dei punti di interruzione.](../../debugger/using-breakpoints.md)

::: moniker-end
## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di esecuzione

::: moniker range="<=vs-2019"

In questa esercitazione nella maggior parte dei casi vengono usati tasti di scelta rapida che rappresentano un modo rapido per eseguire l'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono indicati tra parentesi).

1. Mentre è in pausa nel ciclo nel metodo , premere `For` `Main` **F11** (o scegliere Debug > Esegui istruzione ) due volte per passare alla `SendMessage` chiamata al metodo.

     Dopo aver **premuto F11** due volte, si dovrebbe essere in questa riga di codice:

     `SendMessage(name, a(i))`

1. Premere **F11** ancora una volta per eseguire un'istruzione nel `SendMessage` metodo .

     Il puntatore giallo avanza nel `SendMessage` metodo .

     ![Screenshot che mostra una sessione di debug nell'editor Visual Studio codice con esecuzione sospesa dopo l'esecuzione del metodo 'SendMessage'.](../visual-basic/media/get-started-f11-vb.png)

     F11 corrisponde al comando **Esegui istruzione** e consente di eseguire l'app un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nel dettaglio. Per spostarsi più velocemente nel codice, vengono mostrate anche altre opzioni. Per impostazione predefinita, il debugger ignora il codice non utente. Per altri dettagli, [vedere Just My Code](../../debugger/just-my-code.md).

     Si immagini di aver esaminato il metodo e di voler uscire dal metodo ma rimanere `SendMessage` nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere  + **MAIUSC+F11** (o **Esegui debug > esci da istruzione/uscita**).

     Questo comando riprende l'esecuzione dell'app (e fa avanzare il debugger) fino alla fine del metodo o della funzione corrente.

     Si dovrebbe tornare al `For` ciclo nel metodo , sospeso in corrispondenza della chiamata al metodo `Main` `SendMessage` .

1. Premere **F11** più volte fino a tornare alla chiamata `SendMessage` al metodo .

1. Mentre è in pausa in corrispondenza della chiamata al metodo, premere **F10** (o scegliere **Debug > Esegui istruzione/istruzione)una** sola volta.

     ![Screenshot che mostra una sessione di debug nell'editor Visual Studio codice con l'esecuzione sospesa dopo l'esecuzione della chiamata al metodo 'SendMessage'.](../visual-basic/media/get-started-step-over-vb.png)

     Si noti che questa volta il debugger non esegue un'istruzione nel `SendMessage` metodo . **F10** fa avanzare il debugger senza eseguire le istruzioni nelle funzioni o nei metodi del codice dell'app (il codice rimane in esecuzione). Premendo **F10** nella chiamata al metodo `SendMessage` anziché **F11**, è stato ignorato il codice di implementazione per `SendMessage` (non d'interesse ai fini dell'esercitazione). Per altre informazioni sui diversi modi per spostarsi nel codice, vedere [Esplorare il codice nel debugger.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

::: moniker range=">=vs-2022"

In questo articolo vengono usate le scelte rapide da tastiera, perché è un buon modo per velociare l'esecuzione dell'app nel debugger (i comandi equivalenti, ad esempio i comandi di menu, sono visualizzati tra parentesi).

1. Mentre è in pausa nel ciclo nel metodo , premere `For` `Main` **F11** (o scegliere Debug > Esegui istruzione ) due volte per passare alla `SendMessage` chiamata al metodo.

     Dopo aver **premuto F11** due volte, si dovrebbe essere in questa riga di codice:

     `SendMessage(name, a(i))`

1. Premere **F11** ancora una volta per eseguire un'istruzione nel `SendMessage` metodo .

     Il puntatore giallo avanza nel `SendMessage` metodo .

    :::image type="content" source="media/vs-2022/get-started-f11-vb.png" alt-text="Screenshot che mostra una sessione di debug nell'editor Visual Studio codice con esecuzione sospesa dopo l'esecuzione del metodo 'SendMessage'.":::

     **F11 è** il **comando Istruzione e** fa avanzare l'esecuzione dell'app un'istruzione alla volta. **F11** è un modo efficace per esaminare il flusso di esecuzione nel modo più dettagliato. Per spostarsi più velocemente nel codice, vengono mostrate anche altre opzioni. Per impostazione predefinita, il debugger ignora il codice non utente. Per altri dettagli, [vedere Just My Code](../../debugger/just-my-code.md).

     Si immagini di aver esaminato il metodo e di voler uscire dal metodo ma rimanere `SendMessage` nel debugger. Questa operazione può essere eseguita usando il comando **Esci da istruzione/routine**.

1. Premere  + **MAIUSC+F11** (o **Esegui debug > esci da istruzione/uscita**).

     Questo comando riprende l'esecuzione dell'app (e fa avanzare il debugger) fino alla fine del metodo o della funzione corrente.

     Si dovrebbe tornare al `For` ciclo nel metodo , sospeso in corrispondenza della chiamata al metodo `Main` `SendMessage` .

1. Premere **F11** più volte fino a tornare alla chiamata `SendMessage` al metodo .

1. Mentre è in pausa in corrispondenza della chiamata al metodo, premere **F10** (o scegliere **Debug > Esegui istruzione/istruzione)una** sola volta.

    :::image type="content" source="media/vs-2022/get-started-step-over-vb.png" alt-text="Screenshot che mostra una sessione di debug nell'editor Visual Studio codice con esecuzione sospesa dopo l'esecuzione della chiamata al metodo 'SendMessage'.":::

     Si noti che questa volta il debugger non esegue un'istruzione nel `SendMessage` metodo . **F10** fa avanzare il debugger senza eseguire le istruzioni nelle funzioni o nei metodi del codice dell'app (il codice rimane in esecuzione). Premendo **F10** nella chiamata al metodo `SendMessage` anziché **F11**, è stato ignorato il codice di implementazione per `SendMessage` (non d'interesse ai fini dell'esercitazione). Per altre informazioni sui diversi modi per spostarsi nel codice, vedere [Esplorare il codice nel debugger.](../../debugger/navigating-through-code-with-the-debugger.md)

::: moniker-end

## <a name="navigate-code-using-run-to-click"></a>Esplorare il codice con il pulsante per l'esecuzione fino alla riga selezionata dall'utente

::: moniker range="<=vs-2019"

1. Premere **F5 per** passare di nuovo al punto di interruzione.

1. Nell'editor di codice scorrere verso il basso e passare il puntatore del mouse sul metodo nel metodo fino a quando non viene visualizzato il pulsante verde Esegui fino al clic `Console.WriteLine` `SendMessage` a  :::image type="icon" source="../../debugger/media/dbg-tour-run-to-click.png"::: sinistra. La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

   ![Screenshot che mostra il pulsante Esegui fino al clic con la descrizione comando evidenziata sul lato sinistro della finestra dell'editor di codice.](../visual-basic/media/get-started-run-to-click-vb.png)

   > [!NOTE]
   > Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è una nuova funzionalità di [!include[vs_dev15](../../misc/includes/vs_dev15_md.md)]. Se il pulsante freccia verde non è visualizzato, usare **F11** in questo esempio per far avanzare il debugger nella posizione giusta.

2. Fare clic **sul pulsante Esegui fino a** fare clic su :::image type="icon" source="../../debugger/media/dbg-tour-run-to-click.png"::: .

    Il debugger passa al `Console.WriteLine` metodo .

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

::: moniker-end

::: moniker range=">=vs-2022"

1. Premere **F5 per** passare di nuovo al punto di interruzione.

1. Nell'editor di codice scorrere verso il basso e passare il puntatore del mouse sul metodo nel metodo fino a quando non viene visualizzato il pulsante verde Esegui fino al clic `Console.WriteLine` `SendMessage` a sinistra.  La descrizione comando per il pulsante è "Continua l'esecuzione fino a qui".

   :::image type="content" source="media/vs-2022/get-started-run-to-click-vb.png" alt-text="Screenshot che mostra il pulsante Esegui fino al clic con la descrizione comando evidenziata sul lato sinistro della finestra dell'editor di codice.":::

2. Selezionare il **pulsante Esegui fino a** clic.

    Il debugger passa al `Console.WriteLine` metodo .

    L'uso di questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. Il pulsante per l'**esecuzione fino alla riga selezionata dall'utente** è uno strumento pratico per l'esplorazione rapida all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

::: moniker-end

## <a name="restart-your-app-quickly"></a>Riavviare rapidamente l'app

::: moniker range="<=vs-2019"

Fare clic **sul pulsante** :::image type="icon" source="../../debugger/media/dbg-tour-restart.png"::: Riavvia sulla barra degli strumenti Debug (**CTRL** + **MAIUSC** + **F5**).

Il pulsante **Riavvia** consente di risparmiare tempo rispetto all'arresto dell'app e al riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente in corrispondenza del punto di interruzione impostato in precedenza all'interno del `For` ciclo .

::: moniker-end

::: moniker range=">=vs-2022"

Per riavviare l'app, premere la combinazione di tasti **CTRL**  +  **MAIUSC** F5 per risparmiare tempo rispetto all'arresto dell'app e al  +   riavvio del debugger. Il debugger viene messo in pausa in corrispondenza del primo punto di interruzione raggiunto eseguendo il codice.

Il debugger si arresta nuovamente in corrispondenza del punto di interruzione impostato in precedenza all'interno del `For` ciclo .

::: moniker-end

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

::: moniker range="<=vs-2019"

Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Mentre è in pausa nell'istruzione , passare il puntatore sulla variabile per visualizzarne il valore predefinito, il valore del primo `name += letters[i]` `letters` elemento nella matrice, `"f"c` .

1. Passare quindi il puntatore `name` sulla variabile per visualizzarne il valore corrente, una stringa vuota.

1. Premere **F5** (o **Continua** debug ) alcune volte per eseguire l'iterazione più volte del ciclo, sospendo nuovamente in corrispondenza del punto di interruzione e passando il puntatore del mouse sulla variabile ogni volta per controllarne il >  `For` `name` valore.

     ![Screenshot che mostra l'esecuzione del debug arrestata nell'editor di codice con la variabile "name" evidenziata e un suggerimento dati che mostra il valore "fre".](../visual-basic/media/get-started-data-tip-vb.png)

     Il valore della variabile cambia a ogni iterazione del ciclo, visualizzando i valori `For` di , quindi , e così `f` `fr` `fre` via.

     Spesso, durante il debug, è necessario controllare rapidamente i valori delle proprietà sulle variabili, per vedere se si stanno archiviando i valori previsti, e i suggerimenti dati costituiscono un valido strumento per questa operazione.

::: moniker-end

::: moniker range=">=vs-2022"

Le funzionalità che consentono di esaminare le variabili sono tra le funzionalità più utili del debugger e sono disponibili diversi modi per eseguire questa operazione. Spesso quando si tenta di eseguire il debug di un problema, si tenta di determinare se le variabili includono i valori previsti in un determinato momento.

1. Mentre è in pausa nell'istruzione , passare il puntatore sulla variabile per visualizzarne il valore predefinito, il valore del primo `name += letters[i]` `letters` elemento nella matrice, `"f"c` .

1. Passare quindi il puntatore `name` sulla variabile per visualizzarne il valore corrente, una stringa vuota.

1. Premere **F5** (o **Continua** debug ) alcune volte per eseguire l'iterazione più volte del ciclo, sospendo nuovamente in corrispondenza del punto di interruzione e passando il puntatore del mouse sulla variabile ogni volta per controllarne il >  `For` `name` valore.

     :::image type="content" source="media/vs-2022/get-started-data-tip-vb.png" alt-text="Screenshot che mostra l'esecuzione del debug arrestata nell'editor di codice con la variabile &quot;name&quot; evidenziata e un suggerimento dati che mostra il valore &quot;fre&quot;.":::

     Il valore della variabile cambia a ogni iterazione del ciclo, visualizzando i valori `For` di , quindi , e così `f` `fr` `fre` via.

     Spesso, durante il debug, è necessario controllare rapidamente i valori delle proprietà sulle variabili, per vedere se si stanno archiviando i valori previsti, e i suggerimenti dati costituiscono un valido strumento per questa operazione.

::: moniker-end

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e Variabili locali

::: moniker range="<=vs-2019"

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

    Se è chiuso, aprirlo mentre è in pausa nel debugger scegliendo **Debug** > **Windows** > **Auto.**

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. La finestra **Auto** mostra tutte le variabili usate nella riga corrente o nella riga precedente (vedere la documentazione per il comportamento specifico del linguaggio).

1. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

1. Espandere la `letters` variabile per visualizzare gli elementi in essa contenuti.

     ![Screenshot che mostra la finestra Variabili locali con la variabile "letters" espansa per mostrare il valore e il tipo degli elementi in essa contenuti.](../visual-basic/media/get-started-locals-window-vb.png)

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione corrente.

::: moniker-end

::: moniker range=">=vs-2022"

1. Osservare la finestra **Auto** nella parte inferiore dell'editor di codice.

    Se è chiuso, aprirlo mentre è in  pausa nel debugger scegliendo > **Debug Windows** > **auto.**

    Nella finestra **Auto** vengono visualizzate le variabili e i relativi valori correnti. La finestra **Auto** mostra tutte le variabili usate nella riga corrente o nella riga precedente (vedere la documentazione per il comportamento specifico del linguaggio).

1. Osservare quindi la finestra **Variabili locali** in una scheda accanto alla finestra **Auto**.

1. Espandere la `letters` variabile per visualizzare gli elementi in essa contenuti.

    :::image type="content" source="media/vs-2022/get-started-locals-window-vb.png" alt-text="Screenshot che mostra la finestra Variabili locali con la variabile &quot;letters&quot; espansa per mostrare il valore e il tipo degli elementi in essa contenuti.":::

    La finestra **Variabili locali** mostra le variabili presenti nell'[ambito](https://www.wikipedia.org/wiki/Scope_(computer_science)) corrente, ovvero il contesto di esecuzione corrente.

::: moniker-end

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra principale dell'editor di codice fare clic con il pulsante destro del mouse sulla `name` variabile e scegliere Aggiungi espressioni di **controllo**.

    Viene visualizzata la finestra **Espressione di controllo** nella parte inferiore dell'editor di codice. È possibile usare una finestra **Espressione di controllo** per specificare una variabile (o un'espressione) che si vuole controllare.

    A questo punto, è disponibile un controllo impostato sulla variabile ed è possibile visualizzarne la modifica del `name` valore durante lo spostamento nel debugger. A differenza di altre finestre delle variabili, la finestra **Espressione di controllo** mostra sempre le variabili controllate (che appaiono disattivate quando sono fuori ambito).

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

::: moniker range="<=vs-2019"

1. Mentre l'esecuzione è in pausa nel ciclo `For`, fare clic sulla finestra **Stack di chiamate**, visualizzata per impostazione predefinita nel riquadro inferiore destro.

    Se è chiuso, aprirlo durante la sospensione  nel debugger scegliendo Debug Windows >  > **Stack di chiamate**.

2. Fare **clic su F11** alcune volte fino a quando il debugger non viene sospeso nel `SendMessage` metodo . Osservare la finestra **Stack di chiamate**.

    ![Screenshot che mostra la Visual Studio stack di chiamate con una chiamata al metodo SendMessage evidenziata nella riga superiore.](../visual-basic/media/get-started-call-stack-vb.png)

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `SendMessage` in questa app). La seconda riga indica che `SendMessage` è stato chiamato dal metodo `Main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

::: moniker range=">=vs-2022"

1. Durante la sospensione nel ciclo, fare clic sulla finestra Stack di chiamate, che è aperta per impostazione `For` predefinita nel riquadro inferiore destro. 

    Se è chiuso, aprirlo durante la sospensione  nel debugger scegliendo Debug Windows >  > **Stack di chiamate**.

2. Fare **clic su F11** alcune volte fino a quando il debugger non viene sospeso nel `SendMessage` metodo . Osservare la finestra **Stack di chiamate**.

    :::image type="content" source="media/vs-2022/get-started-call-stack-vb.png" alt-text="Screenshot che mostra la Visual Studio stack di chiamate con una chiamata al metodo SendMessage evidenziata nella riga superiore.":::

    La finestra **Stack di chiamate** visualizza l'ordine in cui vengono chiamati metodi e funzioni. La prima riga visualizza la funzione corrente (il metodo `SendMessage` in questa app). La seconda riga indica che `SendMessage` è stato chiamato dal metodo `Main` e così via.

   > [!NOTE]
   > La finestra **Stack di chiamate** è simile alla prospettiva di debug di alcuni IDE come Eclipse.

    Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

    È possibile fare doppio clic su una riga di codice per visualizzare il codice sorgente e modificare anche l'ambito corrente controllato dal debugger. Questa azione non fa avanzare il debugger.

    È anche possibile usare i menu di scelta rapida nella finestra **Stack di chiamate** per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione nelle funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore** e passare a esaminare il codice sorgente. Per altre informazioni, vedere [Procedura: Esaminare lo stack di chiamate](../../debugger/how-to-use-the-call-stack-window.md).

::: moniker-end

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Premere **F11** due volte per eseguire il `Console.WriteLine` metodo .

1. Con il debugger sospeso nella chiamata al metodo , usare il mouse per afferrare la freccia gialla (il puntatore di esecuzione) a sinistra e spostarlo di una riga verso l'alto, di nuovo `SendMessage` su `Console.WriteLine` .

1. Premere **F11.**

    Il debugger esegue nuovamente il metodo `Console.WriteLine` (visualizzato nell'output della finestra della console).

    Modificando il flusso di esecuzione è possibile eseguire operazioni come testare percorsi di esecuzione del codice diversi o rieseguire il codice senza riavviare il debugger.

    > [!WARNING]
    > Spesso questa funzionalità deve essere usata con attenzione. Nella descrizione comando viene visualizzato un avviso. È anche possibile che vengano visualizzati altri avvisi. Non è possibile ripristinare uno stato precedente dell'applicazione spostando il cursore.

1. Premere **F5** per continuare a eseguire l'app.

    L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice ed esaminare le variabili. Sono disponibili una panoramica delle funzionalità del debugger e collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../../debugger/debugger-feature-tour.md)
