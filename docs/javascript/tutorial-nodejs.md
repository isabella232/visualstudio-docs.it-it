---
title: Creare un'app Node.js ed Express
description: Questa esercitazione illustra come creare una semplice applicazione Node.js usando il framework dell'applicazione Web Express in Visual Studio.
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2bca688977187071b5530911f9aa975e10ceef99
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306527"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app Express in Visual Studio

In questa esercitazione per lo sviluppo in Visual Studio con Node.js ed Express si creerà una semplice applicazione Web Node.js e si aggiungerà codice all'app, quindi si esploreranno alcune funzionalità dell'ambiente IDE e si eseguirà l'app. 

::: moniker range="vs-2017"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2019"

Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2022"

Se non è già stato installato Visual Studio 2022 Preview, passare alla pagina dei download di [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) per installarlo gratuitamente.

::: moniker-end

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto Node.js
> * Aggiungere codice
> * Usare IntelliSense per modificare il codice
> * Eseguire l'app
> * Raggiungere un punto di interruzione nel debugger

## <a name="before-you-begin"></a>Prima di iniziare

Ecco una rapida serie di domande frequenti per presentare alcuni concetti chiave.

### <a name="what-is-nodejs"></a>Che cos'è Node.js?

Node.js è un Java Runtime Environment lato server che esegue JavaScript sul lato server.

### <a name="what-is-npm"></a>Che cos'è npm?

npm è l'applicazione di gestione pacchetti predefinita di Node.js. L'applicazione di gestione pacchetti rende più semplice per i programmatori pubblicare e condividere il codice sorgente delle librerie di Node.js ed è progettata per semplificare l'installazione, l'aggiornamento e la disinstallazione delle librerie.

### <a name="what-is-express"></a>Che cos'è express?

Express è un framework applicazione Web utilizzato come framework server per da Node.js per creare applicazioni Web. Express consente di scegliere framework front-end diversi per creare un'interfaccia utente, ad esempio Pug (in precedenza denominato Jade). In questa esercitazione viene usata l'interfaccia Pug.

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se non è già stato installato Visual Studio 2019, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Se non è installata, è consigliabile installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/) per una migliore compatibilità con framework e librerie esterni. Node.js è progettato per architetture a 32 bit e a 64 bit. Gli Node.js in Visual Studio, inclusi nel carico di lavoro Node.js, supportano entrambe le versioni. Ne è necessario solo uno e Node.js programma di installazione ne supporta solo uno alla volta.
    
    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non rileva un runtime installato, è possibile configurare il progetto in modo che punti al runtime installato nella pagina delle proprietà . Dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Proprietà** e impostare il percorsoNode.exe . È possibile usare un'installazione globale di Node.js o specificare il percorso di un interprete locale in ogni progetto Node.js progetto. 

    Questa esercitazione è stata testata con Node.js 8.10.0.

## <a name="create-a-new-nodejs-project"></a>Creare un nuovo progetto Node.js

Visual Studio gestisce i file per una sola applicazione in un *progetto*. Il progetto include i file di configurazione, le risorse e il codice sorgente.

In questa esercitazione si inizia con un semplice progetto che contiene codice per un'app Express e Node.js.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, digitare **Node.js** e scegliere **Create new Basic Azure Node.js Express 4 application** (Crea nuova applicazione Basic Azure Node.js Express 4) (JavaScript). Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **progetto.** Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Express 4 Node.js Azure di base** e quindi scegliere **OK**.
    ::: moniker-end
    Se non viene visualizzato il modello di progetto **Applicazione Express 4 Node.js Azure di base** è necessario aggiungere il carico di lavoro **Sviluppo Node.js**. Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto nel riquadro destro. Il file di progetto *app.js* verrà aperto nell'editor (riquadro a sinistra).

    ![Struttura del progetto](../javascript/media/tutorial-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Proprietà**. È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json* è un file utilizzato da npm per gestire le dipendenze e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm.](../javascript/npm-package-management.md)

    (5) I file di progetto come *app.js* vengono visualizzati sotto il nodo del progetto. *app.js* è il file di avvio del progetto e per questo motivo viene visualizzata in **grassetto**. Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.

1. Aprire il nodo **npm** e assicurarsi che siano presenti tutti i pacchetti npm necessari.

    Se mancano pacchetti (icona del punto esclamativo), è possibile fare clic con il pulsante destro del mouse sul **nodo npm** e scegliere **Installa pacchetti npm**.

## <a name="add-some-code"></a>Aggiungere codice

L'applicazione usa Pug per il framework JavaScript front-end. Pug usa un codice markup semplice che viene compilato in formato HTML. Pug è impostato come motore di visualizzazione in *app.js*. Il codice che imposta il motore di visualizzazione in *app.js* è `app.set('view engine', 'pug');`.

1. Nel Esplora soluzioni destro aprire la cartella views e quindi *index.pug*.

1. Sostituire il contenuto con il markup seguente.

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

    Il codice precedente viene usato per generare dinamicamente una pagina HTML con un titolo e un messaggio di benvenuto. La pagina include anche il codice per visualizzare un'immagine che cambia ogni volta che si preme un pulsante.

1. Nella cartella routes aprire *index.js*.

1. Aggiungere il codice seguente prima della chiamata a `router.get`:

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

    Questo codice crea un oggetto dati che viene passato alla pagina HTML generata in modo dinamico.

1. Sostituire la chiamata alla funzione `router.get` con il codice seguente:

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    Il codice precedente imposta la pagina corrente usando l'oggetto router di Express ed esegue il rendering della pagina, passando il titolo e l'oggetto dati alla pagina. Il file *index.pug* viene specificato qui come la pagina da caricare quando viene eseguito *index.js*. *index.js* è configurato come la route predefinita nel codice *app.js* (non illustrato).

    Per illustrare diverse funzionalità di Visual Studio, è presente un errore voluto nella riga di codice contenente `res.render`. È necessario correggere l'errore prima di poter eseguire l'app, questa operazione viene eseguita nella sezione successiva.

## <a name="use-intellisense"></a>Usare IntelliSense

IntelliSense è uno strumento di Visual Studio che assiste l'utente durante la scrittura del codice.

1. In *index.js* passare alla riga di codice contenente `res.render`.

1. Posizionare il cursore dopo la stringa `data` e digitare `: get`. IntelliSense visualizzerà la funzione `getData` definita in precedenza nel codice. Selezionare `getData`.

    ![Usare IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. Aggiungere le parentesi per renderla una chiamata di funzione, `getData()` .

1. Rimuovere la virgola (`,`) prima di `"data"`. Verrà visualizzata l'evidenziazione verde della sintassi per l'espressione. Spostare il puntatore del mouse sull'evidenziazione della sintassi.

    ![Visualizzazione di un errore di sintassi](../javascript/media/tutorial-nodejs-syntax-checking.png)

    L'ultima riga di questo messaggio indica che l'interprete JavaScript prevedeva una virgola (`,`).

1. Nel riquadro inferiore fare clic sulla **scheda Elenco** errori e selezionare Compila **+ IntelliSense** per il tipo di problemi segnalati.

    Con il nome del file e il numero di riga verranno visualizzati l'avviso e la relativa descrizione.

    ![Visualizzazione dell'elenco errori](../javascript/media/tutorial-nodejs-error-list.png)

1. Correggere il codice aggiungendo la virgola (`,`) prima di `"data"`.

    Il codice corretto dovrebbe assomigliare al seguente:`res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>Imposta punto di interruzione

L'app verrà eseguita con il debugger di Visual Studio associato. Prima di ciò, è necessario impostare un punto di interruzione.

1. In *index.js* fare clic sul margine sinistro prima della riga di codice seguente per impostare un punto di interruzione:

    `res.render('index', { title: 'Express', "data": getData() });`

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>Eseguire l'applicazione

1. Selezionare la destinazione di debug nella barra degli strumenti Debug, ad esempio **Server Web (Google Chrome)** o **Server Web (Microsoft Edge).**

    ::: moniker range=">=vs-2019"
    ![Selezione della destinazione di debug](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Selezione della destinazione di debug](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    Se Chrome è disponibile nel computer in uso ma non viene visualizzato come opzione, scegliere **Esplora con** dall'elenco a discesa delle destinazioni di debug e selezionare Chrome come destinazione browser predefinita (scegliere **Imposta come predefinito**).

1. Premere **F5** (**Debug** > **Avvia debug**) per eseguire l'applicazione.

    Il debugger si fermerà in corrispondenza del punto di interruzione impostato. È ora possibile esaminare lo stato dell'app.

1. Spostare il puntatore del mouse su `getData` per visualizzarne le proprietà in un suggerimento dati

    ![Esame delle variabili](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. Premere **F5** (**Debug** > **Continua**) per continuare.

    L'app viene aperta in un browser.

    Nella finestra del browser verrà visualizzato il titolo "Express" e nel primo paragrafo verrà visualizzato il messaggio "Welcome to Express".

1. Fare clic sui pulsanti per visualizzare immagini diverse.

    ![App in esecuzione nel browser](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. Chiudere il Web browser.

## <a name="optional-publish-to-azure-app-service"></a>(Facoltativo) Pubblicare in Servizio app di Azure

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto e scegliere **Pubblica**.

   ![Eseguire la pubblicazione nel servizio app di Azure](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. Scegliere **Servizio app di Microsoft Azure**.

    Nella finestra di dialogo **Servizio app** è possibile accedere all'account di Azure e connettersi a sottoscrizioni di Azure esistenti.

1. Seguire i passaggi rimanenti per selezionare una sottoscrizione, scegliere o creare un gruppo di risorse, scegliere o creare un piano di servizio app e quindi, quando richiesto, seguire i passaggi per la pubblicazione in Azure. Per istruzioni più dettagliate, vedere [Pubblicare nel sito Web di Azure usando la distribuzione Web.](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)

1. La finestra **Output** visualizza lo stato della distribuzione in Azure.

    Al termine della distribuzione, l'app viene aperta in un browser in esecuzione in Servizio app di Azure. Fare clic su un pulsante per visualizzare un'immagine.

   ![App in esecuzione in Servizio app di Azure](../javascript/media/tutorial-nodejs-running-in-azure.png)

L'esercitazione è stata completata.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Estensione del servizio di linguaggio AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
