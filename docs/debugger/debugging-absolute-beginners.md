---
title: Debug del codice per principianti
description: Se si esegue il debug per la prima volta, vedere l'articolo alcuni principi che consentono di eseguire l'app in modalità di debug con Visual Studio
ms.custom: ''
ms.date: 07/06/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb37faa194e3c370f92f9a82c7866373dd8f26d3
ms.sourcegitcommit: a6734c4d76dae3d21b55b10f3bc618dfa6b62dea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2018
ms.locfileid: "42623667"
---
# <a name="how-to-debug-for-absolute-beginners"></a>Come eseguire il debug per principianti

Senza ha esito negativo, il codice che scritto dagli sviluppatori di software non esegue sempre ciò che è previsto da eseguire. A volte accade qualcosa di completamente diverso. In questo caso, l'attività successiva consiste nel capire il motivo e anche se è possibile essere tentati di appena mantenere fissare lo nostro codice per le ore, è molto più semplice ed efficiente per usare uno strumento di debug o del debugger.

Un debugger, purtroppo, non qualcosa che può rivelare magicamente nel nostro codice di tutti i problemi o "bug". *Debug* mezzo per eseguire il codice passo a passo in uno strumento di debug, ad esempio Visual Studio, per trovare il punto esatto in cui è stato commesso una programmazione. È quindi conoscere quali le correzioni da apportare al codice e strumenti di debug spesso consentono di apportare modifiche temporanee, pertanto è possibile continuare l'esecuzione del programma.

Uso di un debugger in modo efficace è inoltre una competenza che richiede tempo e procedure consigliate per informazioni su ma in definitiva è un'attività fondamentale tutti gli sviluppatori di software. In questo articolo, quindi, si introducono principi fondamentali di debug e forniscono suggerimenti per iniziare a usare.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>Chiarire il problema da se stessi porre le domande corrette

È utile per chiarire il problema che è stato eseguito nella prima di provare a risolverlo. Prevediamo che già è verificato un problema nel codice, in caso contrario non sarebbe essere qui vuoi scoprire come eseguire il debug! Pertanto, prima di avviare il debug, assicurarsi che è stato identificato il problema che si sta provando a risolvere:

* Che cosa previsto il codice per eseguire?

* Cosa è successo invece?

    Se è verificato un errore (eccezione) durante l'esecuzione dell'app, che può essere positivo. Un'eccezione è un evento imprevisto durante l'esecuzione di codice, in genere un errore di qualche tipo. Uno strumento di debug è possibile accedere alla posizione esatta nel codice in cui si è verificata l'eccezione e può aiutare ad analizzare le possibili correzioni.

    Se si è verificato un altro elemento, che cos'è il sintomo del problema? Già sospetta in cui si è verificato il problema nel codice? Ad esempio, se il codice visualizza il testo, ma il testo non è corretto, sai che i dati non sono valido oppure il codice che imposta il testo visualizzato ha un tipo di bug. Scorrendo il codice in un debugger, è possibile esaminare ogni singola modifica alle variabili di individuare esattamente quando e come vengono assegnati valori non corretti.

## <a name="examine-your-assumptions"></a>Esaminare i presupposti

Prima si esamina un bug o un errore, considerare l'ipotesi che ha effettuato si prevede che un determinato risultato. Presupposti nascosti o sconosciuti possono ostacolare l'identificazione di un problema anche quando si intende corretto la causa del problema in un debugger. È possibile un lungo elenco di possibili presupposti! Ecco alcune domande da porsi alla richiesta di verifica i presupposti.

* Si sta usando l'API a destra (vale a dire, l'oggetto a destra, funzione, metodo o proprietà)? Un'API che sta usando non cosa tu pensi. (Dopo aver esaminato la chiamata all'API nel debugger, correggere la situazione potrebbe essere necessario un viaggio la documentazione per aiutare a identificare l'API corretta.)

* Si sta usando un'API in modo corretto? Forse è utilizzata l'API a destra ma non è stato utilizzato nel modo corretto.

* Il codice contiene eventuali errori di digitazione? Alcuni errori di digitazione, ad esempio un semplice errore di ortografia di un nome di variabile, possono essere difficili da vedere, in particolare quando si lavora con lingue che non richiedono le variabili per essere dichiarata prima che sono abituati.

* È stata si apporta una modifica al codice e si presuppone che non è correlato al problema che si verificano?

* È previsto un oggetto o una variabile per contenere un determinato valore (o un determinato tipo di valore) che è diverso da cosa è successo veramente?

* Si conosce l'intento del codice? È spesso più difficile eseguire il debug di un altro utente del codice. Se non è il codice, è possibile che potrebbe essere necessario dedicare tempo all'apprendimento fa esattamente quali il codice per eseguire il debug in modo efficace.

    > [!TIP]
    > Quando si scrive codice, iniziare in piccolo e iniziare con il codice che funziona! (Codice di esempio buona è utile in questo caso). In alcuni casi, risulta più semplice risolvere un set di grandi dimensioni o complesso di codice, a partire da una piccola parte di codice che illustra le attività di base che si sta tentando di raggiungere. Quindi, è possibile modificare o aggiungere il codice in modo incrementale, il test in ogni punto di presenza di errori.

Messo in dubbio i presupposti, si può ridurre il tempo che necessario per individuare un problema nel codice. È anche possibile ridurre il tempo che necessario per risolvere un problema.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>Esaminare il codice in modalità per individuare dove si è verificato il problema di debug

Quando si eseguono in genere un'app, vengono visualizzati gli errori e risultati non corretti solo dopo l'esecuzione di codice. Un programma può terminare in modo imprevisto senza alcuna informazione sui motivi per cui si.

Esecuzione di un'app all'interno di un debugger, è l'acronimo *modalità di debug*, significa che il debugger monitora attivamente tutto ciò che avviene durante l'esecuzione del programma. Consente inoltre di sospendere l'app in qualsiasi momento per esaminare lo stato e quindi esaminare il codice riga per riga da controllare tutti i dettagli non appena si verifica.

In Visual Studio, è stata immettere la modalità di debug usando **F5** (o il **Debug** > **Avvia debug** comando di menu o **Avvia debug**  sul pulsante ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug")) sulla barra degli strumenti di Debug. Se si verificano tutte le eccezioni, Helper eccezioni di Visual Studio consente di visualizzare il punto esatto in cui l'eccezione si è verificato e fornisce altre informazioni utili.

Se non hai ricevuto un'eccezione, probabilmente hai una buona idea dove cercare il problema nel codice. Ciò in cui si usa *i punti di interruzione* con il debugger per se stessi dare la possibilità di esaminare più attentamente il codice. I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica in cui Visual Studio dovrebbe sospendere il codice in esecuzione in modo che è possibile esaminare i valori delle variabili, o il comportamento della memoria o la sequenza in cui il codice viene eseguito.

In Visual Studio, è possibile impostare rapidamente un punto di interruzione facendo clic sul margine a sinistra accanto a una riga di codice. O posizionare il cursore su una riga e premere **F9**.

Per illustrare questi concetti, si descrivono un codice di esempio che già dispone di diversi bug. Si sta usando c#, ma le funzionalità di debug si applicano a Visual Basic, C++, JavaScript, Python e altri linguaggi supportati.

### <a name="create-a-sample-app-with-some-bugs"></a>Creare un'app di esempio (con alcuni bug)

Successivamente, si creerà un'applicazione che presentano alcuni bug.

1. È necessario avere installato Visual Studio e uno di. **Sviluppo di applicazioni desktop NET** carico di lavoro o di. **NET Core lo sviluppo multipiattaforma** carico di lavoro installato, in base al tipo di app usata da creare.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

    Se è necessario installare il carico di lavoro, ma dispone già di Visual Studio, fare clic su **degli strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il. **Sviluppo di applicazioni desktop NET** (o. **NET Core lo sviluppo multipiattaforma**) carico di lavoro, quindi scegliere **Modify**.

1. Aprire Visual Studio e quindi scegliere **File** > **New** > **progetto**.

1. Scegliere un modello per il codice dell'applicazione.

    Per .NET Framework, nel **nuovo progetto** finestra di dialogo, scegliere **Visual c#**, **Desktop di Windows** dalla sezione dei modelli installati, quindi selezionare il riquadro centrale  **App console (.NET Framework)**.

    Per .NET Core, nelle **nuovo progetto** finestra di dialogo, scegliere **Visual c#**, **.NET Core** dalla sezione dei modelli installati, quindi nel riquadro centrale selezionare  **Console App (.NET Core)**.

    Se non vengono visualizzati questi modelli, è necessario installare il carico di lavoro appropriato (vedere i passaggi precedenti).

1. Nel **Name** , digitare **ConsoleApp FirstApp** e fare clic su **OK**.

    Visual Studio crea il progetto console, che viene visualizzato in Esplora soluzioni nel riquadro di destra.

1. Nelle *Program.cs*, sostituire tutto il codice predefinito con il codice seguente:

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

    Il nostro obiettivo per il codice consiste nel visualizzare il nome galaxy, la distanza di galaxy e il tipo galaxy tutto in un elenco. Per eseguire il debug, è importante comprendere l'intento del codice. Di seguito è riportato il formato per una riga nell'elenco che si desidera mostrare nell'output:

    *nome Galaxy*, *distance*, *tipo galaxy*.

### <a name="run-the-app"></a>Eseguire l'app

1. Premere **F5** o nella **Avvia debug** pulsante ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") nella barra degli strumenti di Debug, che si trova sopra l'editor di codice.

    L'app viene avviata e non sono presenti eccezioni illustrati a Microsoft dal debugger. L'output visualizzato nella finestra della console è, tuttavia, non quello previsto. Ecco l'output previsto:

    ```
    Tadpole  400,  Spiral 
    Pinwheel  25,  Spiral 
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    Tuttavia, verrà visualizzato il invece:

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType 
    Pinwheel  25,  ConsoleApp_FirstApp.GType 
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    Esaminando l'output e il codice, sappiamo che `GType` è il nome della classe che archivia il tipo galaxy. Stiamo tentando di visualizzare il tipo galaxy effettivo (ad esempio, "spirale"), non il nome della classe.

### <a name="debug-the-app"></a>Il debug dell'app

1. Con l'app è ancora in esecuzione, impostare un punto di interruzione facendo clic nel margine sinistro accanto al `Console.WriteLine` chiamata al metodo in questa riga di codice.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }    
    ```

    Quando si imposta il punto di interruzione, viene visualizzato un punto rosso nel margine sinistro.

    Perché abbiamo riscontrato un problema nell'output, verrà avviato il debug osservando il codice precedente che consente di impostare l'output nel debugger.

1. Fare clic sui **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") pulsante sulla barra degli strumenti Debug (**Ctrl** + **MAIUSC**   +  **F5**).

    L'app viene sospesa nel punto di interruzione impostato. L'evidenziazione di colore giallo indica in cui il debugger viene sospeso (la linea gialla di codice non è ancora eseguito).

1. Passare il mouse sul `GalaxyType` variabile sulla destra e quindi a sinistra dell'icona della chiave inglese, espandere `theGalaxy.GalaxyType`. Si può osservare che `GalaxyType` contiene una proprietà `MyGType`, e il valore della proprietà è impostato su `Spiral`.

    ![Esaminare una variabile](../debugger/media/beginners-inspect-variable.png)

    "Spirale" è effettivamente il valore corretto che si aspettava per stampare sulla console. Pertanto è un buon punto di partenza che si può accedere a questo valore in questo codice durante l'esecuzione dell'app. In questo scenario, utilizziamo l'API non corretta. Vedremo se correggere questo problema durante l'esecuzione di codice nel debugger.

1. Nel codice stesso, mentre ancora il debug, posizionare il cursore alla fine della `theGalaxy.GalaxyType` e impostarlo su `theGalaxy.GalaxyType.MyGType`. Anche se è possibile apportare questa modifica, l'editor di codice mostra un errore che indica che non è possibile compilare questo codice.

    ![Errore di sintassi](../debugger/media/beginners-edit.png)

1. Fare clic su **Edit** nel **modifica e continuazione** finestra di messaggio. Viene visualizzato un messaggio di errore a questo punto nel **elenco errori** finestra. L'errore indica che il `'object'` non contiene una definizione per `MyGType`.

    ![Errore di sintassi](../debugger/media/beginners-no-definition.png)

    Anche se è impostata ogni galaxy con un oggetto di tipo `GType` (che contiene il `MGType` proprietà), il debugger non riconosce le `theGalaxy` oggetto come un oggetto di tipo `GType`. Cosa sta succedendo? Si desidera esaminare il codice che imposta il tipo galaxy. Quando si esegue questa operazione, noterete che il `GType` classe ha sicuramente una proprietà di `MyGType`, ma qualcosa non è corretto. Il messaggio di errore sui `object` si rivela le informazioni sul mancato; all'interprete di linguaggio, il tipo viene visualizzato da un oggetto di tipo `object` anziché un oggetto di tipo `GType`.

1. Esaminando il codice correlato all'impostazione del tipo galaxy, trova il `GalaxyType` proprietà del `Galaxy` è specificata come `object` invece di `GType`.

    ```csharp
    public object GalaxyType { get; set; }     
    ```

1. Modificare il codice precedente al seguente:

    ```csharp
    public GType GalaxyType { get; set; }     
    ```

1. Fare clic sui **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") pulsante sulla barra degli strumenti Debug (**Ctrl** + **MAIUSC**   +  **F5**) ricompilare il codice e il riavvio.

    A questo punto, quando il debugger viene sospesa in corrispondenza `Console.WriteLine`, è possibile posizionarsi su `theGalaxy.GalaxyType.MyGType`e riscontrerebbe che il valore viene impostato correttamente.

1. Rimuovere il punto di interruzione facendo clic sul cerchio punto di interruzione nel margine sinistro (o fare clic e scegliere **punto di interruzione** > **Elimina punto di interruzione**), quindi premere **F5** per continuare.

    L'app viene eseguita e viene visualizzato l'output. Sembra abbastanza bene a questo punto, ma si nota una cosa; previsto il galaxy piccola Magellanic Cloud visualizzato come un galaxy irregolare nell'output della console, ma non mostra alcun tipo galaxy affatto.

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

    Questo codice è in cui è impostato il tipo galaxy, pertanto desideriamo richiedere uno sguardo più da vicino.

1. Fare clic sui **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") pulsante sulla barra degli strumenti Debug (**Ctrl** + **MAIUSC**   +  **F5**) da riavviare.

    Il debugger sospende nella riga di codice in cui è impostato il punto di interruzione.  

1. Passare il mouse su di `type` variabile. Viene visualizzato un valore di `S` (dopo il codice carattere). Si è interessati a un valore di `I`, dal momento che si sa che è un tipo galaxy irregolare.

1. Premere **F5** e passare il mouse su di `type` variabile anche in questo caso. Ripetere questo passaggio finché non viene visualizzato un valore pari `I` nella `type` variabile.

    ![Esaminare una variabile](../debugger/media/beginners-inspecting-data.png)

1. A questo punto, premere **F11** (**Debug** > **Esegui istruzione** oppure la **Esegui istruzione** pulsante sulla barra degli strumenti di Debug).

    **F11** fa avanzare il debugger (ed esegue codice) un'istruzione alla volta. **F10** (**Esegui istruzione/routine**) è un comando analogo ed entrambe risultano estremamente utili per imparare a usare il debugger.

1. Premere **F11** finché non si interrompe nella riga di codice nel `switch` istruzione per il valore di 'I'. In questo caso, viene riscontrato un problema clear derivante da un errore di digitazione. Previsto il codice per passare al punto in cui imposta `MyGType` come un irregolari galaxy tipo, ma il debugger invece ignora questo codice completamente e viene sospesa in corrispondenza di `default` sezione il `switch` istruzione.

    ![Trovare un errore di digitazione](../debugger/media/beginners-typo.png)

    Esaminando il codice, viene visualizzato un errore di digitazione nel `case 'l'` istruzione. Deve essere `case 'I'`.

1. Fare clic su nel codice `case 'l'` e sostituirla con `case 'I'`.

1. Rimuovere il punto di interruzione e quindi scegliere il **riavviare** per riavviare l'app.

    A questo punto, vengono corretti i bug e viene visualizzato l'Output previsto.

    Premere un tasto qualsiasi per terminare l'app.

## <a name="summary"></a>Riepilogo

Quando viene riscontrato un problema, usare il debugger e [eseguire i comandi](../debugger/navigating-through-code-with-the-debugger.md) , ad esempio **F10** e **F11** per trovare l'area di codice con il problema.

> [!NOTE]
> Se è difficile da identificare l'area di codice in cui si verifica il problema, impostare un punto di interruzione nel codice in esecuzione prima che si verifichi il problema e quindi usare tali comandi fino a quando non viene riscontrato il problema manifesto. È anche possibile usare [i punti di traccia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) per registrare i messaggi per il **Output** finestra. Da esaminando i messaggi registrati (e osservando i messaggi che non sono stati ancora registrati!), è spesso possibile isolare l'area di codice con il problema. È possibile ripetere questo processo più volte per restringere la ricerca.

Quando si trova l'area di codice con il problema, utilizzare il debugger per esaminare. Per trovare la causa di un problema, esaminare il codice problema durante l'esecuzione dell'app nel debugger:

* [Esaminare le variabili](../debugger/view-data-values-in-data-tips-in-the-code-editor.md) e verificare se contengono il tipo di valori che devono contenere. Se un valore non valido, scoprire dove è stato impostato il valore non valido (per individuare dove è stato impostato il valore, potrebbe essere necessario il riavvio del debugger, esaminare i [stack di chiamate](../debugger/how-to-use-the-call-stack-window.md), o entrambi).

* Controllare se l'applicazione è in esecuzione il codice che si prevede. (Ad esempio, nell'applicazione di esempio, è previsto il codice per l'istruzione switch impostare il tipo galaxy a irregolari, ma l'app ignorati il codice a causa di errore di digitazione.)

> [!TIP]
> Utilizzare un debugger per individuare i bug. Uno strumento di debug può individuare i bug *automaticamente* solo se ne conosce l'intento del codice. Uno strumento può solo conoscere la finalità del codice se dallo sviluppatore, esprimere tale finalità. La scrittura [unit test](../test/improve-code-quality.md) è come farlo.

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si sono appreso alcuni concetti fondamentali di debug generali. Successivamente, è possibile iniziare a imparare a eseguire il debug con Visual Studio.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
