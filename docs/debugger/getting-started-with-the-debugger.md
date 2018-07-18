---
title: Informazioni sul debug tramite il debugger di Visual Studio
ms.description: Learn how to start the Visual Studio debugger, step through code, and inspect data.
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: 62734c0d-a75a-4576-8f73-0e97c19280e1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1144e7e33709510cb03ed02cb62020f81e8e8b62
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36303146"
---
# <a name="tutorial-learn-to-debug-using-visual-studio"></a>: Esercitazione eseguire il debug usando Visual Studio

In questo argomento presenta le funzionalità del debugger di Visual Studio in una procedura dettagliata. Se si desidera una visualizzazione di alto livello delle funzionalità di debug, vedere [Debugger Feature Tour](../debugger/debugger-feature-tour.md). Quando si *il debug dell'app*, in genere significa che si esegue l'applicazione con il debugger collegato. Quando si esegue questa operazione, il debugger fornisce diversi modi per ottenere informazioni sulle attività del codice mentre è in esecuzione. È possibile esaminare il codice ed esaminare i valori archiviati nelle variabili, è possibile impostare espressioni di controllo per le variabili per vedere quando vengono modificati i valori, è possibile esaminare il percorso di esecuzione del codice, et al. Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo argomento.

Possono letti lungo per fare riferimento alle funzionalità del debugger o, è possibile scaricare l'esempio completo usato nel Tour delle funzionalità e seguire i passaggi manualmente. Per scaricare il codice di esempio e seguire la procedura, passare a [Demo Visualizzatore foto](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

|         |         |
|---------|---------|
|  ![icona della telecamera](../install/media/video-icon.png "Guardare un video")  |    [Guardare un video](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugger-Feature-tour-of-Visual-studio-2017-sqwiwLD6D_1111787171) sull'esecuzione del debug che illustra una procedura simile. |

Anche se l'app demo è c#, le funzionalità sono applicabili a C++, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (se diversamente specificato).

In questa esercitazione si eseguono le attività seguenti:

> [!div class="checklist"]
> * Avviare il debugger e raggiungere punti di interruzione.
> * Informazioni sui comandi per avanzare nel codice nel debugger
> * Ispezione delle variabili nelle finestre del debugger e i suggerimenti dati
> * Esaminare lo stack di chiamate
> * Usare l'Helper eccezioni

## <a name="prerequisites"></a>Prerequisiti

* È necessario disporre di Visual Studio 2017 installato e il. **Sviluppo di applicazioni desktop NET** carico di lavoro.

    Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) per installarlo gratuitamente.

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, fare clic sul collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto** (selezionare **File** > **Nuovo** > **Progetto**). Verrà avviato il Programma di installazione di Visual Studio. Scegliere il. **Sviluppo di applicazioni desktop NET** carico di lavoro, quindi scegliere **Modify**.

## <a name="start-the-debugger"></a>Avviare il debugger.

1. Per proseguire con questa procedura in Visual Studio, scaricare il codice di esempio [in questa pagina](https://code.msdn.microsoft.com/windowsdesktop/WPF-Photo-Viewer-Demo-be75662a).

    > [!IMPORTANT]
    > È necessario installare Visual Studio con il carico di lavoro di sviluppo per Desktop .NET per eseguire l'app che verrà usato nella demo.

2. Decomprimere il progetto.

3. Aprire Visual Studio e selezionare il **File > Apri** menu comando e quindi scegliere **progetto/soluzione**e quindi aprire la cartella in cui è stato scaricato il progetto.

     ![Aprire il progetto di esempio](../debugger/media/dbg-tour-open-project.png "Apri progetto")

3. Aprire la Demo Visualizzatore foto di WPF > c# cartella, scegliere il *photoapp.sln* e selezionare **Open**.

     Il progetto viene aperto in Visual Studio. Esplora soluzioni nel riquadro destro mostra tutti i file di progetto.

    ![I file di Esplora soluzioni](../debugger/media/dbg-tour-solution-explorer.png "Esplora soluzioni")

4. Premere **F5** (**Debug > Avvia debug**) o nella **Avvia debug** pulsante ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug ") nella barra degli strumenti Debug.

     ![App Visualizzatore foto](../debugger/media/dbg-tour-wpf-app.png "App Visualizzatore di foto")

     F5 avvia l'app con il debugger collegato al processo dell'app, ma a destra, a questo punto è ancora stato aggiunto alcun punto di interruzione o eseguita alcuna operazione particolare per esaminare il codice. Quindi, solo caricamento dell'app e verranno visualizzate le immagini di foto.

     In questa panoramica verranno Esaminiamo più da vicino l'app usando il debugger e ottenere un quadro il debugger di funzionalità.

5. Arrestare il debugger premendo l'arresto rossa ![Termina debug](../debugger/media/dbg-tour-stop-debugging.png "arresta debug") pulsante.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Impostare un punto di interruzione e avviare il debugger

Per eseguire il debug, è necessario avviare l'app con il debugger collegato al processo dell'app.

1. Nel `MainWindow` costruttore di MainWindow.xaml.cs, impostare un punto di interruzione facendo clic sul margine sinistro della prima riga del codice.

     ![Impostare un punto di interruzione](../debugger/media/dbg-tour-set-a-breakpoint.gif "SetABreakPoint")

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice. 

6. Premere **F5** o nella **Avvia debug** pulsante, l'app viene avviata e il debugger viene eseguito per la riga di codice in cui è impostato il punto di interruzione.

    La freccia gialla rappresenta l'istruzione in cui il debugger ha sospeso, che anche sospende l'esecuzione di app nella stessa fase (questa istruzione non è ancora eseguito).

    F5 continua l'esecuzione dell'app per il punto di interruzione successivo. (Se l'app non è ancora in esecuzione, F5 viene avviato il debugger e si interrompe al primo punto di interruzione).

    I punti di interruzione sono una funzionalità molto utile quando si conosce la riga di codice o nella sezione di codice che si desidera esaminare in dettaglio.

## <a name="optional-restart-your-app-quickly"></a>(Facoltativo) Riavviare l'app rapidamente

Fare clic sui **riavviare** ![riavviare App](../debugger/media/dbg-tour-restart.png "RestartApp") pulsante sulla barra degli strumenti Debug (**Ctrl** + **MAIUSC**   +  **F5**).

Quando si preme **riavviare**, consentono di risparmiare tempo e l'arresto dell'app e riavviare il debugger. Il debugger si fermerà in corrispondenza il primo punto di interruzione viene raggiunto mediante l'esecuzione di codice.

Il debugger si arresta nuovamente nel punto di interruzione è impostato, nel `MainWindow` costruttore.

## <a name="navigate-code-in-the-debugger-using-step-commands"></a>Esplorare il codice nel debugger tramite i comandi di passaggio

In genere, usiamo i tasti di scelta rapida in questo caso, perché è un buon metodo per ottenere rapidamente in esecuzione l'app nel debugger (comandi equivalenti, ad esempio menu i comandi vengono visualizzati tra parentesi).

1. Premere **F11** (**Debug > Esegui istruzione**) due volte per anticipare l'esecuzione dell'app per la `InitializeComponent()` (funzione).

     ![Usare F11 per codice Esegui istruzione](../debugger/media/dbg-tour-f11.png "F11 Esegui istruzione")

     F11 è il **Esegui istruzione** comando e sposta in avanti l'app esecuzione un'istruzione alla volta. F11 è un buon metodo per esaminare il flusso di esecuzione nella maggior parte dei dettagli. (Per spostare più velocemente tramite il codice, viene illustrato alcune altre opzioni inoltre.) Per impostazione predefinita, il debugger ignora codice non utente (se si desidera visualizzare ulteriori dettagli, vedere [Just My Code](../debugger/just-my-code.md)).

     >[!NOTE]
     > Nel codice gestito, si verrà visualizzato una finestra di dialogo che chiede se si desidera ricevere una notifica quando automaticamente l'istruzione/routine delle proprietà e operatori (comportamento predefinito). Se si desidera modificare l'impostazione in un secondo momento, disabilitare **Esegui istruzione/routine di proprietà e operatori** impostazione nelle **strumenti > Opzioni** menu sotto **debug**.

2. Premere **F10** (**Debug > Esegui istruzione/routine**) più volte fino a quando il debugger si arresta sulla prima riga di codice nel `OnApplicationStartup` gestore dell'evento.

     ![Usare F10 per codice Esegui istruzione/routine](../debugger/media/dbg-tour-f10-step-over.png "F10 Esegui istruzione/routine")

     F10 fa avanzare il debugger senza eseguire istruzioni di funzioni o metodi nel codice dell'app (il codice viene ancora eseguito). Premendo F10 il `InitializeComponent` chiamata al metodo (anziché F11), viene ignorato il codice di implementazione per `InitializeComponent` (quali ad esempio se si non sta interessano subito).

## <a name="step-into-a-property"></a>Passaggio in una proprietà

1. Il debugger è in pausa su questa riga di codice:

    ````c#
    mainWindow.Photos.Path = Environment.CurrentDirectory + "\\images";
    ````

    Fare clic sulla riga di codice e scegliere **Esegui istruzione specifica**, quindi **SDKSamples.ImageSample.PhotoCollection.Path.set**

     ![Usare il passaggio a funzionalità specifiche](../debugger/media/dbg-tour-step-into-specific.png "Esegui istruzione specifica")

    Come accennato in precedenza, per impostazione predefinita il debugger ignora le proprietà gestite e i campi, ma il **Esegui istruzione specifica** comando consente di eseguire l'override di questo comportamento. Per il momento si vuole osservare cosa accade quando il `Path.set` esecuzioni setter di proprietà. **Esegui istruzione specifica** arrivati al `Path.set` qui il codice.

     ![risultato dell'istruzione specifica](../debugger/media/dbg-tour-step-into-specific-2.png "Esegui istruzione specifica")

     Il `Update` metodo nel codice seguente esegue la ricerca può sembrare interessante, in questo caso consente di usano il debugger per il codice di chiusura.

5. Passare il mouse sul `Update` metodo fino al verde **Esegui fino al clic** pulsante ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") viene visualizzata a sinistra.

     ![Usare l'esecuzione a fare clic su funzionalità](../debugger/media/dbg-tour-run-to-click-2.png "eseguire fa clic su")

    >  [!NOTE]
    > Il **Esegui fino al clic** pulsante è stato introdotto in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]. Se il pulsante freccia verde non è visualizzato, utilizzare F11 in questo esempio per far avanzare il debugger.

6. Fare clic sul **Esegui fino al fare clic su** pulsante ![Esegui fino al fare clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

    Tramite questo pulsante è simile all'impostazione di un punto di interruzione temporaneo. **Esegui fino al clic** è utile per ottenere rapidamente all'interno di un'area visibile del codice dell'app (è possibile fare clic in qualsiasi file aperto).

    Fa avanzare il debugger di `Update` implementazione del metodo.

7. Premere **F11** per eseguire l'istruzione di `Update` (metodo).

     ![Risultato dell'esecuzione di istruzioni al metodo di aggiornamento](../debugger/media/dbg-tour-update-method.png "passaggio nel metodo di aggiornamento")

    In questo caso, troviamo un codice più che sembra interessante; l'app stia ottenendo tutti. *jpg* file che si trova in una determinata directory e quindi la creazione di un oggetto foto per ogni file. Questo codice ci offre un'ottima opportunità per avviare la verifica lo stato dell'app (variabili) con il debugger. Facciamo che nelle sezioni successive di questa esercitazione.

    Funzionalità che consentono di controllare le variabili sono una delle funzionalità più utili del debugger, ed esistono diversi modi per farlo. Spesso, quando si tenta di eseguire il debug di un problema, si sta tentando di scoprire se le variabili archiviano i valori che si prevede possano avere in un determinato momento.

## <a name="examine-the-call-stack"></a>Esaminare lo stack di chiamate

Durante la pausa il `Update` metodo, fare clic sui **Stack di chiamate** finestra, per impostazione predefinita è aperto nel riquadro inferiore destro.

![Esaminare lo stack di chiamate](../debugger/media/dbg-tour-call-stack.png "ExamineCallStack")

Il **Stack di chiamate** finestra Mostra l'ordine in cui vengono introduzione chiamate i metodi e le funzioni. La prima riga visualizza la funzione corrente (la `Update` metodo nell'app per la presentazione). La seconda riga indica che `Update` è stato chiamato dal `Path.set` proprietà e così via.

>  [!NOTE]
> Il **Stack di chiamate** finestra è simile alla prospettiva di Debug in alcuni ambienti di sviluppo integrato, ad esempio Eclipse.

Lo stack di chiamate è un ottimo modo per esaminare e comprendere il flusso di esecuzione di un'app.

È possibile fare doppio clic su una riga di codice per passare osservare che il codice sorgente e che viene modificato anche l'ambito corrente viene controllato dal debugger. Questa azione non fa avanzare il debugger.

È anche possibile usare i menu di scelta rapida dal **Stack di chiamate** finestra per eseguire altre operazioni. Ad esempio, è possibile inserire i punti di interruzione in funzioni specificate, far avanzare il debugger usando **Esegui fino al cursore**e passare a esaminare il codice sorgente. Per altre informazioni, vedere [procedura: esaminare lo Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).

## <a name="step-out"></a>Esci da istruzione

Si supponga di che aver esaminando il `Update` metodo in Data.cs e si vuole ricavare la funzione, ma rimangono nel debugger. È possibile farlo usando il **Esci da istruzione /** comando.

1. Premere **Shift** + **F11** (o **Debug > Esci da istruzione**).

     Questo comando riprende l'esecuzione di app (e fa avanzare il debugger) fino a quando non restituisce la funzione corrente.

     Verrà visualizzata nuovamente la `Update` chiamata al metodo in Data.cs.

2. Premere **Shift** + **F11** anche in questo caso e il debugger passa lo stack di chiamate al `OnApplicationStartup` gestore dell'evento.

## <a name="run-to-cursor"></a>Esecuzione fino al cursore

1. Scegliere il **Termina debug** pulsante rosso ![arresta debug](../debugger/media/dbg-tour-stop-debugging.png "arresta debug") oppure **MAIUSC** + **F5** .

2. Nel `Update` metodo nella *Data.cs*, fare doppio clic il `Add` metodo chiamare e scegliere **Esegui fino al cursore**. Questo comando avvia il debug e imposta un punto di interruzione temporaneo nella riga di codice corrente.

     ![Usare l'esecuzione alla funzionalità di cursore](../debugger/media/dbg-tour-run-to-cursor.png "Esegui fino al cursore")

    Deve essere interrotta nel punto di interruzione nel `MainWindow` (dal momento che è il primo punto di interruzione è impostato).

3. Premere **F5** per passare alle `Add` metodo in cui è selezionata **Esegui fino al cursore**.

    Questo comando è utile quando si modifica del codice e si vuole impostare un punto di interruzione temporanea rapidamente e avviare il debugger.

## <a name="change-the-execution-flow"></a>Modificare il flusso di esecuzione

1. Il debugger è in pausa sul `Add` chiamata al metodo, utilizzare il mouse per trascinare la freccia gialla (il puntatore di esecuzione) a sinistra e spostare la freccia gialla alto di una riga per il `foreach` ciclo.

     ![Spostare il puntatore di esecuzione](../debugger/media/dbg-tour-move-the-execution-pointer.gif "spostare il puntatore di esecuzione")

    Se si modifica il flusso di esecuzione, è possibile eseguire operazioni come percorsi di esecuzione di codice diversi di test o eseguire di nuovo codice senza riavviare il debugger.

2. A questo punto, premere **F5**.

    È possibile visualizzare le immagini aggiunte alla finestra dell'app. Poiché si sta eseguendo nuovamente nel codice il `foreach` ciclo, alcune delle immagini sono state aggiunte due volte!

    > [!WARNING]
    > Spesso è necessario prestare attenzione con questa funzionalità, e viene visualizzato un avviso nella descrizione comando. È possibile visualizzare altri avvisi, troppo. Spostare il puntatore del mouse non è possibile ripristinare l'applicazione a uno stato precedente di app.

## <a name="inspect-variables-with-data-tips"></a>Esaminare le variabili con i suggerimenti dati

1. Aprire *Data.cs* nell'app Demo di Visualizzatore foto, fare doppio clic il `private void Update` dichiarazione di funzione e scegliere **Esegui fino al cursore** (arrestare l'app prima di tutto se è già in esecuzione).

    Si sospende l'app con il debugger collegato. Ciò consente di esaminare il relativo stato.

2. Passare il mouse sul `Add` metodo chiamare e fare clic sul **Esegui fino al clic** pulsante ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick").

3. A questo punto, passare il mouse sopra l'oggetto File (`f`) e viene visualizzato il valore di proprietà predefinito, il nome del file *immissione sul mercato 031. jpg*.

     ![Visualizzare un suggerimento dati](../debugger/media/dbg-tour-data-tips.gif "consente di visualizzare un suggerimento dati")

4. Espandere l'oggetto per visualizzare tutte le relative proprietà, ad esempio il `FullPath` proprietà.

    Spesso, durante il debug, si desidera un modo rapido per verificare i valori delle proprietà sugli oggetti e i suggerimenti dati sono un buon metodo per eseguire questa operazione.

    > [!TIP]
    > Nei linguaggi più supportati, è possibile modificare il codice all'interno di una sessione di debugger se si trova qualcosa che si desidera modificare. Per altre informazioni, vedi [modifica e continuazione](../debugger/edit-and-continue.md). Per usare tale funzionalità in questa app, tuttavia, è innanzitutto necessario aggiornare la versione dell'app di .NET Framework.

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Esaminare le variabili con le finestre Auto e variabili locali

1. Esaminare i **Auto** finestra nella parte inferiore dell'editor del codice.

     ![Esaminare le variabili nella finestra Auto](../debugger/media/dbg-tour-autos-window.png "finestra Auto")

    Nel **Auto** finestra, noterete che le variabili e il relativo valore corrente. Il **Auto** finestra Mostra tutte le variabili usate nella riga corrente o nella riga precedente (In C++, la finestra Mostra le variabili in tre righe di codice precedenti. Vedere la documentazione per il comportamento specifico del linguaggio).

    > [!NOTE]
    > In JavaScript, il **variabili locali** finestra è supportata ma non le **Auto** finestra.

2. Esaminare quindi le **variabili locali** finestra.

    Il **variabili locali** finestra Mostra le variabili che sono nell'ambito corrente.

    ![Esaminare le variabili nella finestra variabili locali](../debugger/media/dbg-tour-locals-window.png "finestra variabili locali")

    Attualmente, il `this` oggetto e l'oggetto File (`f`) sono nell'ambito corrente. Per altre informazioni, vedi [esaminare le variabili in auto e variabili locali Windows](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Impostare un'espressione di controllo

1. Nella finestra dell'editor di codice principale, fare doppio clic su oggetto File (`f`) e scegliere **Aggiungi espressione di controllo**.

    È possibile usare una **Watch** per specificare una variabile (o un'espressione) che si desidera tenere d'occhio nella finestra.

    A questo punto, si dispone di un'espressione di controllo impostato sul `File` oggetto ed è possibile visualizzarne il valore cambia quando sposta tramite il debugger. A differenza di altre finestre delle variabili, il **Watch** finestra Mostra sempre le variabili che sta controllando (è disattivati quando fuori ambito).

2. Nel `Add` metodo, fare clic su verde ![eseguire fa clic su](../debugger/media/dbg-tour-run-to-click.png "RunToClick") nuovamente clic sul pulsante (o premere alcune volte F11) di avanzare il `foreach` ciclo.

    ![Impostare un'espressione di controllo in una variabile](../debugger/media/dbg-tour-watch-window.png "finestra Espressioni di controllo")

    È anche possibile visualizzare l'immagine prima richiedere di essere aggiunti alla finestra principale di esecuzione dell'app di esempio, ma ciò accade in un thread di app diversi, in modo che le immagini potrebbero non essere ancora visibili.

    Per altre informazioni, vedere [impostare un'espressione di controllo usando le espressioni di controllo e controllo immediato Windows](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-an-exception"></a>Esaminare un'eccezione

1. Nella finestra dell'applicazione in esecuzione, eliminare il testo nel **tracciato** casella di input e selezionare il **modifica** pulsante.

     ![Generare un'eccezione viene generata](../debugger/media/dbg-tour-cause-an-exception.png "generano un'eccezione")

     L'app genera un'eccezione e il debugger consente di visualizzare la riga di codice che ha generato l'eccezione.

     ![Helper eccezioni](../debugger/media/dbg-tour-exception-helper.png "Helper eccezioni")

     In questo caso, il **Helper eccezioni** Mostra un `System.ArgumentException` e un messaggio di errore indicante che il percorso non è un modulo valido. Pertanto, sappiamo che si è verificato l'errore su un argomento di metodo o funzione.

     In questo esempio, il `DirectoryInfo` chiamata è stato assegnato l'errore nella archiviati in una stringa vuota di `value` variabile. (Mouse `value` per visualizzare una stringa vuota.)

     Gestore di eccezioni è un'ottima funzionalità che consentono di eseguire il debug degli errori. È anche possibile eseguire operazioni come visualizzare i dettagli dell'errore e aggiungere un'espressione di controllo dal gestore di eccezioni. In alternativa, se necessario, è possibile modificare le condizioni per l'eccezione specifica.

    >  [!NOTE]
    > L'Helper eccezioni consente di sostituire le informazioni sulle eccezioni in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

2. Espandere la **impostazioni eccezioni** nodo per visualizzare altre opzioni su come gestire questo tipo di eccezione, ma è necessario modificare alcun valore per questa presentazione.

3. Premere **F5** per continuare con l'esecuzione dell'app.

Per altre informazioni sulle funzionalità del debugger, vedere [Debugger suggerimenti e trucchi](../debugger/debugger-tips-and-tricks.md).

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è appreso come avviare il debugger, eseguire il codice e controllare le variabili. È possibile ottenere una panoramica sulle funzionalità del debugger oltre a collegamenti a ulteriori informazioni.

> [!div class="nextstepaction"]
> [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
