---
title: Debug del codice per principianti
description: Principi utili per l'esecuzione di un'app in modalità di debug con Visual Studio per chi esegue il debug per la prima volta
ms.date: 07/06/2018
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f5cfe112aff36910ca4b4861d3a65cc7ea61655
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65679378"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Debug per principianti

Senza dubbio, il codice scritto dagli sviluppatori di software non sempre funziona come previsto. A volte, funziona in modo completamente diverso. Quando ciò accade, l'attività successiva consiste nel capirne il motivo e, anche se si sarebbe tentati di passare ore a controllare ogni riga di codice, l'uso di uno strumento di debug, o debugger, si rivelerà molto più semplice ed efficiente.

Un debugger, purtroppo, non rivela magicamente tutti i problemi o "bug" presenti nel codice. Per *debug* si intende l'esecuzione passo a passo del codice in uno strumento di debug, ad esempio Visual Studio, per trovare il punto esatto in cui è stato commesso un errore di programmazione. Si comprenderà quindi quali correzioni apportare al codice. Gli strumenti di debug spesso consentono inoltre di apportare modifiche temporanee in modo da poter continuare l'esecuzione del programma.

L'uso efficiente di un debugger è anche una competenza che si acquisisce con il tempo e la pratica ed è in realtà un'attività fondamentale per qualsiasi sviluppatore di software. In questo articolo vengono pertanto presentati i principi di base del debug e vengono offerti suggerimenti per iniziare.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Chiarire il problema ponendosi le domande giuste

Prima di provare a risolverlo, è utile chiarire il problema riscontrato. Probabilmente si è già riscontrato un problema nel codice, altrimenti non si starebbe leggendo questo articolo per cercare di capire come risolverlo. Prima di iniziare il debug, assicurarsi quindi di aver identificato il problema che si sta tentando di risolvere:

* Qual era il comportamento previsto del codice?

* Cosa è successo invece?

    Se durante l'esecuzione dell'app si è verificato un errore (eccezione), può essere un buon segno. Un'eccezione è un evento imprevisto riscontrato durante l'esecuzione del codice, in genere un errore di qualche tipo. Uno strumento di debug è in grado di passare al punto esatto nel codice in cui si è verificata l'eccezione e può aiutare ad analizzare le possibili correzioni.

    Se è successo qualcos'altro, qual è il sintomo del problema? Si ha già un'idea del punto in cui si è verificato il problema nel codice? Nel caso, ad esempio, di codice che visualizza del testo, la visualizzazione di testo non corretto indica che i dati non sono corretti oppure che il codice che ha impostato il testo visualizzato contiene un bug di qualche tipo. L'esecuzione del codice istruzione dopo istruzione in un debugger consente di esaminare ogni modifica alle variabili per comprendere esattamente quando e come vengono assegnati valori non corretti.

## <a name="examine-your-assumptions"></a>Esaminare i presupposti

Prima si analizzare un bug o un errore, riflettere sui presupposti che hanno fatto in modo che ci si aspettasse un determinato risultato. Presupposti nascosti o sconosciuti possono ostacolare l'identificazione di un problema anche quando la causa del problema risulta evidente in un debugger. L'elenco dei possibili presupposti potrebbe essere lungo. Di seguito sono riportate alcune domande da porsi per verificare i propri presupposti.

* Si sta usando l'API giusta, ovvero l'oggetto, la funzione, il metodo o la proprietà corretti? L'API che si sta usando potrebbe avere un funzionamento diverso da quello che ci si aspetta. Dopo aver esaminato la chiamata all'API nel debugger, può essere necessario consultare la documentazione per identificare l'API corretta.

* L'API viene usata correttamente? Forse è stata usata l'API giusta, ma non nel modo corretto.

* Il codice contiene errori di digitazione? Alcuni errori di digitazione, ad esempio un semplice errore di ortografia nel nome di una variabile, possono essere difficili da vedere, specialmente quando si lavora con linguaggi in cui non è necessario dichiarare le variabili prima di usarle.

* È stata apportata una modifica al codice e si presuppone che non sia correlata al problema che si verifica?

* Un oggetto o una variabile doveva contenere un determinato valore o un determinato tipo di valore diverso da quello che in realtà contiene?

* Si è a conoscenza della finalità del codice? Eseguire il debug del codice di un altro sviluppatore è spesso più difficile. Se non si tratta del proprio codice, può essere necessario dedicare un po' di tempo a conoscere il codice prima di poterne eseguire il debug in modo efficace.

    > [!TIP]
    > Quando si scrive il codice, iniziare con un codice semplice che funzioni. Un buon codice di esempio è utile in questo caso. A volte è più facile correggere un set di codici complessi o di grandi dimensioni partendo da una piccola parte di codice che dimostra l'attività di base che si sta tentando di ottenere. È quindi possibile modificare o aggiungere codice in modo incrementale, testando l'eventuale presenza di errori in corrispondenza di ogni punto.

Riflettendo sui presupposti, si può ridurre il tempo necessario per individuare un problema nel codice e quello necessario per risolverlo.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Eseguire il codice istruzione dopo istruzione in modalità di debug per individuare il punto in cui si è verificato il problema

Quando si esegue un'app normalmente, errori e risultati non corretti sono visibili solo al termine dell'esecuzione del codice. Un programma potrebbe anche essere chiuso in modo imprevisto senza alcuna indicazione sui motivi.

L'esecuzione di un'app all'interno di un debugger, o in *modalità di debug*, consente al debugger di monitorare attivamente tutto ciò che accade durante l'esecuzione del programma. Consente anche di sospendere l'app in un punto qualsiasi per esaminarne lo stato e di eseguire quindi il codice riga per riga per controllare ogni dettaglio durante l'esecuzione.

In Visual Studio si entra in modalità di debug usando **F5** oppure il comando di menu **Debug** > **Avvia debug** o il pulsante **Avvia debug** ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") nella barra degli strumenti di debug. In caso di eccezioni, l'Helper eccezioni di Visual Studio visualizza il punto esatto in cui si è verificata l'eccezione e offre altre informazioni utili. Per altre informazioni su come gestire le eccezioni nel codice, vedere [Tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md).

Se non è stata restituita un'eccezione, probabilmente si ha già un'idea di dove cercare il problema nel codice. In questi casi si usano i *punti di interruzione* con il debugger per avere l'opportunità di esaminare il codice più attentamente. I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio deve sospendere il codice in esecuzione in modo da consentire di esaminare i valori delle variabili, il comportamento della memoria o la sequenza di esecuzione del codice.

In Visual Studio è possibile impostare rapidamente un punto di interruzione facendo clic sul margine sinistro accanto a una riga di codice oppure si può posizionare il cursore su una riga e premere **F9**.

Per illustrare questi concetti si userà un codice di esempio che contiene già diversi bug. Verrà usato C#, ma le funzionalità di debug si applicano a Visual Basic, C++, JavaScript, Python e altri linguaggi supportati.

### <a name="create-a-sample-app-with-some-bugs"></a>Creare un'app di esempio (con alcuni bug)

Verrà creata un'applicazione con alcuni bug.

1. È necessario avere installato Visual Studio e il carico di lavoro **Sviluppo per desktop .NET** o **Sviluppo multipiattaforma .NET Core**, a seconda del tipo di app che si vuole creare.

    Se Visual Studio non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/)  per installarlo gratuitamente.

    Per installare il carico di lavoro avendo già Visual Studio, fare clic su **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET** o **Sviluppo multipiattaforma .NET Core** e quindi **Modifica**.

1. Aprire Visual Studio.

    ::: moniker range=">=vs-2019"
    Nella finestra iniziale scegliere **Crea un nuovo progetto**. Digitare **console** nella casella di ricerca per filtrare i risultati, scegliere **App console (.NET Framework)** o **App console (.NET Core)**. Scegliere **Avanti**. Digitare un nome di progetto, ad esempio **ConsoleApp-FirstApp** e fare clic su **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra **Nuovo progetto** in **Visual C#** scegliere **App console** e quindi nel riquadro centrale scegliere **App console (.NET Framework)** o **App console (.NET Core)**. Digitare un nome, ad esempio **ConsoleApp-FirstApp** e fare clic su **OK**.
    ::: moniker-end

    Se il modello di progetto **App console (.NET Framework)** o **App console (.NET Core)** non viene visualizzato, passare a **Strumenti** > **Ottieni strumenti e funzionalità**. Viene aperto il programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET** o **Sviluppo multipiattaforma .NET Core** e quindi scegliere **Modifica**.

    Visual Studio crea il progetto della console che viene visualizzato nel riquadro destro di Esplora soluzioni.

1. In *Program.cs* sostituire tutto il codice predefinito con il codice seguente:

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }

            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };

                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }

                // Expected Output:
                //  Tadpole  400,  Spiral
                //  Pinwheel  25,  Spiral
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }

        public class Galaxy
        {
            public string Name { get; set; }

            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }

        }

        public class GType
        {
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    La finalità di questo codice è visualizzare il nome della galassia, la distanza dalla galassia e il tipo di galassia, tutto in un elenco. Per eseguire il debug, è importante comprendere la finalità del codice. Di seguito è riportato il formato per una riga dell'elenco che si vuole visualizzare nell'output:

    *nome galassia*, *distanza*, *tipo di galassia*.

### <a name="run-the-app"></a>Eseguire l'app

1. Premere **F5** o il pulsante **Avvia debug** ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") nella barra degli strumenti di debug che si trova sopra l'editor del codice.

    L'app viene avviata e il debugger non visualizza alcuna eccezione. Tuttavia, l'output visualizzato nella finestra della console è diverso da quanto ci si aspetta. L'output previsto è:

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Ciò che viene invece visualizzato è:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Esaminando l'output e il codice, si comprende che `GType` è il nome della classe che archivia il tipo di galassia. Ciò che si sta cercando di visualizzare è il tipo di galassia (ad esempio, "Spiral"), non il nome della classe.

### <a name="debug-the-app"></a>Eseguire il debug dell'app

1. Con l'app ancora in esecuzione, impostare un punto di interruzione facendo clic nel margine sinistro accanto alla chiamata al metodo `Console.WriteLine` in questa riga di codice.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    Quando si imposta il punto di interruzione, viene visualizzato un punto rosso nel margine sinistro.

    Poiché si è riscontrato un problema nell'output, il debug verrà avviato esaminando il codice precedente che imposta l'output nel debugger.

1. Fare clic sul pulsante **Riavvia** ![Riavvia app](../debugger/media/dbg-tour-restart.png "Riavvia app") nella barra degli strumenti di debug (**CTRL** + **MAIUSC** + **F5**).

    L'app verrà sospesa in corrispondenza del punto di interruzione impostato. L'evidenziazione di colore giallo indica il punto in cui il debugger viene sospeso (la riga di codice gialla non è ancora stata eseguita).

1. Passare il puntatore sulla variabile `GalaxyType` a destra e quindi, a sinistra dell'icona a forma di chiave inglese, espandere `theGalaxy.GalaxyType`. Si può osservare che `GalaxyType` contiene una proprietà `MyGType` e il valore della proprietà è impostato su `Spiral`.

    ![Ispezionare una variabile](../debugger/media/beginners-inspect-variable.png)

    "Spiral" è effettivamente il valore corretto che ci si aspettava di stampare nella console. La possibilità di accedere a questo valore nel codice durante l'esecuzione dell'app è pertanto un buon punto di partenza. In questo scenario viene usata l'API non corretta. Si vedrà come risolvere questo problema durante l'esecuzione del codice nel debugger.

1. Nello stesso codice, durante il debug, posizionare il cursore alla fine di `theGalaxy.GalaxyType` e modificarlo in `theGalaxy.GalaxyType.MyGType`. Anche se questa modifica è consentita, l'editor del codice visualizza un errore che indica l'impossibilità di compilare il codice.

    ![Errore di sintassi](../debugger/media/beginners-edit.png)

1. Fare clic su **Modifica** nella finestra di messaggio **Modifica e continuazione**. Un messaggio di errore viene ora visualizzato nella finestra **Elenco errori**. L'errore indica che `'object'` non contiene una definizione per `MyGType`.

    ![Errore di sintassi](../debugger/media/beginners-no-definition.png)

    Anche se ogni galassia è stata impostata con un oggetto di tipo `GType` (che include la proprietà `MyGType`), il debugger non riconosce l'oggetto `theGalaxy` come oggetto di tipo `GType`. Cosa è successo? Esaminare tutto il codice che imposta il tipo di galassia. Durante questa operazione, si noterà che la classe `GType` include certamente una proprietà `MyGType`, ma qualcosa non va. Il messaggio di errore relativo a `object` è l'indizio; per l'interprete del linguaggio, il tipo è un oggetto di tipo `object` anziché un oggetto di tipo `GType`.

1. Esaminando il codice relativo all'impostazione del tipo di galassia, si nota che la proprietà `GalaxyType` della classe `Galaxy` è specificata come `object` invece di `GType`.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. Modificare il codice precedente in questo modo:

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. Fare clic sul pulsante **Riavvia** ![Riavvia app](../debugger/media/dbg-tour-restart.png "Riavvia app") nella barra degli strumenti di debug (**CTRL** + **MAIUSC** + **F5**) per ricompilare il codice e riavviare.

    Ora, quando il debugger viene sospeso in corrispondenza di `Console.WriteLine`, passando il puntatore su `theGalaxy.GalaxyType.MyGType` si noterà che il valore è impostato correttamente.

1. Rimuovere il punto di interruzione facendo clic sul relativo cerchio nel margine sinistro oppure fare clic con il pulsante destro del mouse e scegliere **Punto di interruzione** > **Elimina punto di interruzione**, quindi premere **F5** per continuare.

    L'app viene eseguita e visualizza l'output. Ora sembra tutto corretto, ma si nota qualcosa. Ci si aspettava che la galassia "Small Magellanic Cloud" venisse indicata nell'output della console come galassia di tipo "Irregular", ma il tipo di galassia non viene indicato affatto.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. Impostare un punto di interruzione in questa riga di codice.

    ```csharp
    public GType(char type)
    ```

    Il tipo di galassia viene impostato in questo codice. Esaminarlo quindi in dettaglio.

1. Fare clic sul pulsante **Riavvia** ![Riavvia app](../debugger/media/dbg-tour-restart.png "Riavvia app") nella barra degli strumenti di debug (**CTRL** + **MAIUSC** + **F5**) per riavviare.

    Il debugger viene sospeso sulla riga di codice in cui è stato impostato il punto di interruzione.

1. Passare il puntatore sulla variabile `type`. Si noterà il valore `S` (dopo il codice carattere). Si è interessati al valore `I`, dal momento che si sa che si tratta di un tipo di galassia irregolare.

1. Premere **F5** e passare di nuovo il puntatore sulla variabile `type`. Ripetere questo passaggio finché non si vedrà il valore `I` nella variabile `type`.

    ![Ispezionare una variabile](../debugger/media/beginners-inspecting-data.png)

1. Premere ora **F11** (**Debug** > **Esegui istruzione** o il pulsante **Esegui istruzione** nella barra degli strumenti di debug).

    **F11** fa avanzare il debugger (ed esegue il codice) un'istruzione alla volta. **F10** (**Esegui istruzione/routine**) è un comando simile ed entrambi sono estremamente utili quando si impara a usare il debugger.

1. Premere **F11** fino all'arresto in corrispondenza della riga di codice nell'istruzione `switch` per il valore "I". Qui si noterà un evidente problema derivante da un errore di digitazione. Ci si aspettava che il codice avanzasse fino al punto in cui `MyGType` viene impostato come galassia di tipo "Irregular". Il debugger invece ignora completamente questo codice e viene sospeso nella sezione `default` dell'istruzione `switch`.

    ![Individuare un errore di digitazione](../debugger/media/beginners-typo.png)

    Esaminando il codice, si nota un errore di digitazione nell'istruzione `case 'l'`. Quella corretta è `case 'I'`.

1. Fare clic sul codice per `case 'l'` e sostituirla con `case 'I'`.

1. Rimuovere il punto di interruzione e quindi fare clic sul pulsante **Riavvia** per riavviare l'app.

    A questo punto i bug sono stati risolti e viene visualizzato l'output previsto.

    Premere un tasto qualsiasi per terminare l'app.

## <a name="summary"></a>Riepilogo

Quando si nota un problema, usare il debugger e i [comandi di esecuzione](../debugger/navigating-through-code-with-the-debugger.md), ad esempio **F10** e **F11**, per trovare l'area di codice con il problema.

> [!NOTE]
> Se è difficile identificare l'area di codice in cui si verifica il problema, impostare un punto di interruzione nel codice in esecuzione prima del punto in cui si verifica il problema e quindi usare i comandi di esecuzione fino a individuarlo. È anche possibile usare [punti di analisi](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) per registrare i messaggi nella finestra **Output**. Esaminando i messaggi registrati (e prestando particolare attenzione a quelli non ancora registrati), è spesso possibile isolare l'area di codice con il problema. Per restringere la ricerca potrebbe essere necessario ripetere il processo diverse volte.

Dopo aver trovato l'area di codice con il problema, usare il debugger per analizzarlo. Per trovare la causa di un problema, ispezionare il codice problematico durante l'esecuzione dell'app nel debugger:

* [Esaminare le variabili](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) e verificare se contengono il tipo di valori che devono contenere. Se si trova un valore non valido, individuare il punto in cui è stato impostato. A questo scopo, può essere necessario riavviare il debugger, controllare lo [stack di chiamate](../debugger/how-to-use-the-call-stack-window.md) o entrambi.

* Controllare se l'applicazione esegue il codice previsto. Nell'applicazione di esempio il codice per l'istruzione switch doveva ad esempio impostare il tipo di galassia su "Irregular", ma l'app ignorava il codice a causa di un errore di digitazione.

> [!TIP]
> Un debugger aiuta a trovare i bug. Uno strumento di debug sarà in grado di individuare i bug *automaticamente* solo se conosce la finalità del codice. Uno strumento può conoscere la finalità del codice solo se lo sviluppatore esprime tale finalità. Per farlo, occorre scrivere [unit test](../test/improve-code-quality.md).

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si sono appresi alcuni concetti di debug generali. In seguito, è possibile apprendere di più sul debugger.

> [!div class="nextstepaction"]
> [Presentazione del debugger](../debugger/debugger-feature-tour.md)
