---
title: Creare un'app Node.js e React
description: Informazioni su come creare un progetto Node.js'applicazione Web da un Visual Studio personalizzato.
ms.custom: vs-acquisition
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 55672b542bc2418cc1c5b2b7cf300072e8215695
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635900"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app React in Visual Studio

Visual Studio consente di creare con facilità un progetto Node.js e di provare IntelliSense e altre funzionalità incorporate che supportano Node.js. In questa esercitazione per Visual Studio si crea un progetto di applicazione web Node.js da un modello di Visual Studio. Quindi si crea un'app semplice usando React.

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto Node.js
> * Aggiungere pacchetti npm
> * Aggiungere codice React all'app
> * Eseguire il transpile in JSX
> * Collegare il debugger

## <a name="before-you-begin"></a>Prima di iniziare

Ecco una rapida serie di domande frequenti per presentare alcuni concetti chiave.

### <a name="what-is-nodejs"></a>Che cos'è Node.js?

Node.js è un Java Runtime Environment lato server che esegue JavaScript sul lato server.

### <a name="what-is-npm"></a>Che cos'è npm?

npm è l'applicazione di gestione pacchetti predefinita di Node.js. L'applicazione di gestione pacchetti rende più semplice per i programmatori pubblicare e condividere il codice sorgente delle librerie di Node.js ed è progettata per semplificare l'installazione, l'aggiornamento e la disinstallazione delle librerie.

### <a name="what-is-react"></a>Cos'è React?

React è un framework front-end per creare un'interfaccia utente.

### <a name="what-is-jsx"></a>Cos'è JSX?

JSX è un'estensione della sintassi JavaScript in genere usata con React per descrivere gli elementi dell'interfaccia utente. Prima di poter essere eseguito in un browser, il codice JSX deve essere convertito tramite transpile in codice JavaScript semplice.

### <a name="what-is-webpack"></a>Cos'è webpack?

webpack aggrega i file JavaScript per consentirne l'esecuzione in un browser. Può anche trasformare o creare pacchetti di altri asset e risorse. Viene spesso usato per specificare un compilatore, ad esempio Babel o TypeScript, per convertire tramite transpile il codice JSX o TypeScript in codice JavaScript semplice.

## <a name="prerequisites"></a>Prerequisiti

* È necessario che siano installati Visual Studio e il carico di lavoro di sviluppo Node.js.

    ::: moniker range=">=vs-2019"
    Se non è ancora stato installato Visual Studio 2019, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se Visual Studio 2017 non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
    ::: moniker-end

    Se è necessario installare il carico di lavoro ma Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

    ![Carico di lavoro Node.js nel programma di installazione di Visual Studio](../ide/media/quickstart-nodejs-workload.png)

* Il runtime di Node.js deve essere installato.

    Questa esercitazione è stata testata con la versione 12.6.2.

    Se non è installato, è consigliabile installare la versione LTS dal sito Web [ diNode.js](https://nodejs.org/en/download/) per una migliore compatibilità con framework e librerie esterni. Node.js è progettato per architetture a 32 bit e a 64 bit. Gli Node.js in Visual Studio, inclusi nel carico di lavoro Node.js, supportano entrambe le versioni. Ne è necessario solo uno e Node.js programma di installazione ne supporta solo uno alla volta.

    In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non rileva un runtime installato, è possibile configurare il progetto in modo che punti al runtime installato nella pagina delle proprietà (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto, scegliere Proprietà **(o** premere **ALT**  +   **INVIO)** e impostare il percorsoNode.exe ). È possibile usare un'installazione globale di Node.js oppure è possibile specificare il percorso di un interprete locale in ogni progetto Node.js progetto. 

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa creare un progetto di applicazione Web Node.js.

1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    ::: moniker range=">=vs-2019"
    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, **digitareNode.js** e quindi scegliere Blank Node.js Web Application - JavaScript (Applicazione Web vuota - **JavaScript).** Anche se questa esercitazione usa il compilatore TypeScript, i passaggi richiedono di iniziare con il **modello JavaScript.**
    
    Nella finestra di dialogo visualizzata scegliere **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, digitare il nome **NodejsWebAppBlank**, quindi scegliere **OK**.
    ::: moniker-end
    Se il modello di progetto Applicazione **Web Node.js** vuoto non è visualizzato, è necessario aggiungere il carico di **Node.js di** sviluppo. Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto.

    ![Progetto Node.js in Esplora soluzioni](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo Proprietà **(o** **premendo ALT**  +  **INVIO).** È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json* è un file utilizzato da npm per gestire le dipendenze e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm.](../javascript/npm-package-management.md)

    (5) I file di progetto come *server.js* vengono visualizzati sotto il nodo del progetto. *server.js* è il file di avvio del progetto e per questo motivo viene visualizzato in **grassetto**. Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.

## <a name="add-npm-packages"></a>Aggiungere pacchetti npm

Per essere eseguita correttamente, l'app richiede vari moduli npm.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. In Esplora soluzioni (riquadro destro), fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e scegliere **Installa nuovi pacchetti npm**.

    Nella finestra di dialogo **Installa nuovi pacchetti npm** è possibile scegliere di installare la versione più recente dei pacchetti o specificare la versione desiderata. Se si sceglie di installare la versione corrente di questi pacchetti, ma si verificano errori imprevisti in un secondo momento, è possibile installare le versioni esatte dei pacchetti descritte più avanti in questi passaggi.

1. Nella finestra di dialogo **Installa nuovi pacchetti npm** cercare il pacchetto react e selezionare **Installa pacchetto** per installarlo.

    ![Installa nuovi pacchetti npm](../javascript/media/tutorial-nodejs-react-install-package.png)

    Selezionare la finestra **Output** per visualizzare lo stato di avanzamento dell'installazione del pacchetto (selezionare **Npm** nel campo **Mostra output di**). Dopo l'installazione il pacchetto viene visualizzato sotto il nodo **npm**.

    Il file *package.json* del progetto viene aggiornato con le nuove informazioni sul pacchetto, inclusa la versione del pacchetto.

1. Invece di usare l'interfaccia utente per cercare e aggiungere il resto dei pacchetti uno alla volta, incollare il codice seguente in *package.json*. A tale scopo, aggiungere una sezione `dependencies` con il codice seguente:

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    Se la versione del modello vuoto in uso contiene già una sezione `dependencies`, sostituirla con il codice JSON precedente. Per altre informazioni sull'uso di questo file, vedere [configurazione di package.json.](../javascript/configure-packages-with-package-json.md)

1. Salvare le modifiche.

1. Fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e **scegliere Installa pacchetti npm**.

    Questo comando esegue direttamente il comando npm install.

    Nel riquadro inferiore selezionare la finestra **Output** per vedere lo stato di avanzamento dell'installazione dei pacchetti. L'installazione potrebbe richiedere alcuni minuti e potrebbe non essere possibile visualizzare immediatamente i risultati. Per visualizzare l'output, assicurarsi di selezionare **Npm** nel campo **Mostra output di** della finestra **Output**. Per aprire la finestra, scegliere **Visualizza**  >  **Output** o premere **CTRL**  +    +  **ALT+O.**

    Ecco come appaiono i moduli npm in Esplora soluzioni dopo l'installazione.

    ![Pacchetti npm](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > Se si preferisce installare pacchetti npm o comandi node.js dalla riga di comando, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**. Per installare i pacchetti, usare i comandi Node.js standard.

## <a name="add-project-files"></a>Aggiungere file di progetto

In questa procedura si aggiungono quattro nuovi file al progetto.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Per questa app semplice i nuovi file di progetto vengono aggiunti nella radice del progetto. Nella maggior parte delle app i file vengono aggiunti a sottocartelle e i riferimenti al percorso relativo vengono modificati di conseguenza.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto **NodejsWebAppBlank** e scegliere Aggiungi nuovo  >  **elemento** (o premere **CTRL**  +  **MAIUSC**  +  **A).**

1. Nella finestra **di dialogo Aggiungi** nuovo elemento scegliere File **JSX TypeScript,** digitare il nome *app.tsx* e selezionare **Aggiungi** o **OK.**

1. Ripetere questi passaggi per aggiungere *webpack-config.js*. Invece di un file JSX TypeScript, scegliere **file JavaScript**.

1. Ripetere gli stessi passaggi per aggiungere *index.html* al progetto. Invece di un file JavaScript, scegliere **File HTML**.

1. Ripetere gli stessi passaggi per aggiungere *tsconfig.json* al progetto. Invece di un file JavaScript, scegliere **File di configurazione JSON per TypeScript**.

## <a name="add-app-code"></a>Aggiungere il codice dell'app

1. Aprire il file *server.js* e sostituire il codice esistente con quello seguente:

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Il codice precedente usa Express per avviare Node.js come server di applicazioni web. Questo codice imposta la porta sul numero di porta configurato nelle proprietà del progetto (per impostazione predefinita, nelle proprietà è configurata la porta 1337). Per aprire le proprietà del progetto fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

1. Aprire *app.tsx* e aggiungere il codice seguente:

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    export class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Il codice precedente usa la sintassi JSX e React per visualizzare un messaggio semplice.

1. Aprire *index.html* e sostituire la sezione **body** con il codice seguente:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Questa pagina HTML carica *app-bundle.js*, che contiene il codice JSX e React convertito tramite transpile in codice JavaScript semplice. Attualmente *app-bundle.js* è un file vuoto. Nella sezione successiva, si configurano le opzioni per eseguire il transpile del codice.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configurare le opzioni di webpack e del compilatore TypeScript

Nei passaggi precedenti è stato aggiunto al progetto *webpack-config.js*. Ora si aggiunge il codice di configurazione webpack. Si aggiunge una configurazione webpack semplice, che specifica un file di input (*app.tsx*) e un file di output (*app-bundle.js*) per la creazione di bundle e il transpile da JSX a codice JavaScript semplice. Per l'esecuzione del transpile si configurano anche alcune opzioni del compilatore TypeScript. Questo codice è una configurazione di base, che ha lo scopo di presentare webpack e il compilatore TypeScript.

1. In Esplora soluzioni aprire *webpack-config.js* e aggiungere il codice seguente.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Il codice di configurazione webpack indica a webpack di usare il caricatore TypeScript per eseguire il transpile di JSX.

1. Aprire *tsconfig.json* e sostituire il codice predefinito con il seguente, che specifica le opzioni del compilatore TypeScript:

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.tsx* viene specificato come file di origine.

## <a name="transpile-the-jsx"></a>Eseguire il transpile di JSX

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

1. Al prompt dei comandi digitare il seguente comando:

    `node_modules\.bin\webpack ./app.tsx --config webpack-config.js`

    Il risultato viene visualizzato nella finestra del prompt dei comandi.

    ![Eseguire webpack](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    Se invece dell'output precedente vengono visualizzati degli errori, è necessario risolverli prima di poter eseguire l'app. Una causa degli errori può essere il fatto che le versioni dei pacchetti npm sono diverse da quelle visualizzate in questa esercitazione. Un modo per correggere gli errori consiste nell'usare le versioni esatte visualizzate nei passaggi precedenti. Se una o più di queste versioni dei pacchetti sono state deprecate e generano errori, potrebbe essere necessario installare una versione più recente per correggere gli errori. Per informazioni sull'uso di *package.json* per controllare le versioni del pacchetto npm, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md).

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** cartella esistente, quindi scegliere  >  la *cartella dist* e **scegliere Seleziona cartella**.

    Visual Studio aggiunge al progetto la cartella *dist* che contiene *app-bundle.js* e *app-bundle.js.map*.

1. Aprire *app-bundle.js* per visualizzare il codice JavaScript di cui è stato eseguito il transpile.

1. Se viene richiesto di ricaricare i file modificati esternamente, selezionare **Sì a tutti**.

    ![Caricare i file modificati](../javascript/media/tutorial-nodejs-react-reload-files.png)

Ogni volta che si apportano modifiche ad *app.tsx* è necessario eseguire nuovamente il comando webpack. Per automatizzare questo passaggio, aggiungere uno script di compilazione per il transpile di JSX.

## <a name="add-a-build-script-to-transpile-the-jsx"></a>Aggiungere uno script di compilazione per il transpile di JSX

A partire da Visual Studio 2019, è necessario uno script di compilazione. Invece di eseguire il transpile di JSX dalla riga di comando (come illustrato nella sezione precedente), è possibile eseguirlo durante la compilazione da Visual Studio.

* Aprire *package.json* e aggiungere la sezione seguente dopo la sezione `dependencies`:

   ```json
   "scripts": {
    "build": "webpack-cli ./app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>Eseguire l'app

1. Selezionare **Server Web (Google Chrome)** o **Server Web (Microsoft Edge)** come destinazione di debug corrente.

    ::: moniker range=">=vs-2019"
    ![Selezionare Chrome come destinazione di debug](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Selezionare Chrome come destinazione di debug](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Se Chrome è disponibile nel computer in uso ma non viene visualizzato come opzione, scegliere **Esplora con** dall'elenco a discesa delle destinazioni di debug e selezionare Chrome come destinazione browser predefinita (scegliere **Imposta come predefinito**).

1. Per eseguire l'app, premere **F5** (**Debug** > **Avvia debug**) o fare clic sul pulsante con la freccia verde.

    Viene visualizzata una finestra della console Node.js che indica la porta sulla quale è in ascolto il debugger.

    Visual Studio avvia l'app eseguendo il file di avvio *server.js*.

    ![Eseguire React nel browser](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Chiudere la finestra del browser.

1. Chiudere la finestra della console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Impostare un punto di interruzione ed eseguire l'app

1. In *server.js* fare clic nella barra a sinistra della dichiarazione `staticPath` per impostare un punto di interruzione:

    ![Screenshot della finestra Visual Studio codice per server.js. Un punto rosso nella barra di spostamento a sinistra indica che è impostato un punto di interruzione per la dichiarazione staticPath.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Per eseguire l'applicazione, premere **F5** (**Debug** > **Avvia debug**).

    Il debugger sospende l'esecuzione nel punto di interruzione impostato (l'istruzione corrente è contrassegnata in giallo). A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Premere **F5** per continuare con l'esecuzione dell'app.

1. Se si vuole usare Chrome Strumenti di sviluppo o F12 Tools per Microsoft Edge, premere **F12**. È possibile usare questi strumenti per esaminare il modello DOM e interagire con l'app mediante la console JavaScript.

1. Chiudere il Web browser e la console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Impostare e raggiungere un punto di interruzione nel codice React lato client

Nella sezione precedente il debugger è stato associato al codice Node.js lato server. Per associare il debugger da Visual Studio e accedere a punti di interruzione nel codice React lato client, è necessario che il debugger identifichi il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

### <a name="prepare-the-browser-for-debugging"></a>Preparare il browser per il debug

::: moniker range=">=vs-2019"
Per questo scenario, usare Microsoft Edge (Chromium), attualmente denominato **Microsoft Edge Beta** nell'IDE o Chrome.
::: moniker-end
::: moniker range="vs-2017"
Per questo scenario, usare Chrome.
::: moniker-end

1. Chiudere tutte le finestre per il browser di destinazione.

   Altre istanze del browser possono impedire l'apertura del browser con il debug abilitato. Le estensioni del browser potrebbero essere in esecuzione e impedire la modalità di debug completa, quindi potrebbe essere necessario aprire Gestione attività per trovare istanze impreviste di Chrome.

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (Chromium), arrestare anche tutte le istanze di Chrome. Poiché entrambi i browser condividono la codebase del cromo, questo offre i risultati migliori.
   ::: moniker-end

2. Avviare il browser con il debug abilitato.

    ::: moniker range=">=vs-2019"
    A partire da Visual Studio 2019, è possibile impostare il flag all'avvio del browser selezionando Esplora con > dalla barra degli strumenti `--remote-debugging-port=9222` **Debug,**  quindi scegliendo Aggiungi e quindi impostando il flag nel campo Argomenti.  Usare un nome descrittivo diverso per il browser, ad esempio **Edge with Debugging (Edge con debug)** **o Chrome with Debugging (Chrome con debug).** Per informazioni dettagliate, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-v16.2).

    ![Impostare il browser per l'apertura con il debug abilitato](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    In alternativa, aprire il **comando Esegui** dal Windows **start** (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `msedge --remote-debugging-port=9222`

    o

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Verrà avviato il browser con il debug abilitato.

    L'app non è ancora in esecuzione, quindi si ottiene una pagina vuota del browser.

### <a name="attach-the-debugger-to-client-side-script"></a>Collegare il debugger allo script lato client

1. Passare a Visual Studio e quindi impostare un punto di interruzione nel codice sorgente, *app-bundle.js* *o app.tsx*.

    Per *app-bundle.js*, impostare il punto di interruzione nella `render()` funzione come illustrato nella figura seguente:

    ![Screenshot della finestra Visual Studio codice per app-bundle.js. Un punto rosso nella barra di spostamento a sinistra indica che nella funzione di rendering è impostato un punto di interruzione.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Per trovare la `render()` funzione nel file di *app-bundle.js* transpiled, usare **CTRL** + **F** (**Modifica** Ricerca  >  **e sostituisci** Ricerca  >  **rapida**).

    Per *app.tsx*, impostare il punto di interruzione all'interno `render()` della funzione nell'istruzione `return` .

    ![Screenshot della finestra Visual Studio codice per app.tsx. Un punto rosso nella barra di spostamento a sinistra indica che è impostato un punto di interruzione nell'istruzione return della funzione di rendering.](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. Se si imposta il punto di interruzione nel file con estensione *tsx* (anzichéapp-bundle.js *),* è necessario aggiornare *webpack-config.js*. Sostituire il codice seguente:

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    con questo codice:

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    Si tratta di un'impostazione di solo sviluppo per abilitare il debug in Visual Studio. Questa impostazione consente di eseguire l'override dei riferimenti generati nel file source map, *app-bundle.js.map,* durante la compilazione dell'app. Per impostazione predefinita, i riferimenti webpack nel file source map includono il prefisso *webpack:///,* che impedisce Visual Studio trovare il file di origine, *app.tsx.* In particolare, quando si apporta questa modifica, il riferimento al file di origine, *app.tsx,* viene modificato *da webpack:///./app.tsx* a *./app.tsx,* che abilita il debug.

3. Selezionare il browser di destinazione come destinazione di debug in Visual Studio, quindi premere **CTRL** + **F5** (**Debug** Avvia senza eseguire debug ) per eseguire l'app  >  nel browser.

    ::: moniker range=">=vs-2019"
    Se è stata creata una configurazione del browser con un nome descrittivo, sceglierne una come destinazione di debug.
    ::: moniker-end

    L'app viene aperta in una nuova scheda del browser.

4. Scegliere **Debug**  >  **Attach to Process (Esegui** debug connessione a processo) o premere **CTRL**  +  **ALT**  +  **P.**

    > [!TIP]
    > A partire da Visual Studio 2017, una volta che ci si connette al processo la prima volta seguendo questi passaggi, è possibile ricollegare rapidamente allo stesso processo scegliendo **Debug** Ricollegare a processo  >   (o premere **MAIUSC**  +  **ALT**  +  **P).**

5. Nella finestra **di dialogo Associa a** processo ottenere un elenco filtrato di istanze del browser a cui è possibile connettersi.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere il debugger corretto per il browser di destinazione, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** nel campo Collega a, digitare **chrome** o **edge** nella casella del filtro per filtrare i risultati della ricerca. 
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere Webkit code (Codice **Webkit)** nel campo **Attach to** (Collega a) e digitare **chrome** nella casella del filtro per filtrare i risultati della ricerca.
    ::: moniker-end

6. Selezionare il processo del browser con la porta host corretta (localhost in questo esempio) e selezionare **Collega**.

    La porta (1337) può essere visualizzata anche nel campo **Titolo** per consentire di selezionare l'istanza corretta del browser.

    ::: moniker range=">=vs-2019"
    Nell'esempio seguente viene illustrato l'aspetto del browser Microsoft Edge (Chromium).

    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili ai Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se il debugger non è associato e viene visualizzato il messaggio "Impossibile connettersi al processo. Un'operazione non è valida nello stato corrente.", usare il Gestione attività per chiudere tutte le istanze del browser di destinazione prima di avviare il browser in modalità di debug. Le estensioni del browser potrebbero essere in esecuzione e impedire la modalità di debug completo.

7. Dato che il codice con il punto di interruzione è già stato eseguito, aggiornare la pagina del browser per raggiungere il punto di interruzione.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**). Per altre informazioni sulle funzionalità di debug di base, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

    È possibile che venga raggiunto il punto di interruzione *inapp-bundle.js* o nella relativa posizione mappata in *app.tsx,* a seconda dei passaggi seguiti in precedenza, insieme all'ambiente e allo stato del browser. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

   * Se è necessario inserire un'interruzione nel codice in *app.tsx*, ma non è possibile eseguire questa operazione, usare **Associa a processo** come descritto nei passaggi precedenti per associare il debugger. Assicurarsi che l'ambiente sia configurato correttamente:

      * Sono state chiuse tutte le istanze del browser, incluse le estensioni di Chrome (usando il Gestione attività), in modo da poter eseguire il browser in modalità di debug. Assicurarsi di avviare il browser in modalità di debug.

      * Assicurarsi che il file source map includa un riferimento a *./app.tsx* e non *webpack:///./app.tsx*, impedendo così al debugger Visual Studio di individuare *app.tsx.*
       In alternativa, se è necessario interrompere il codice in *app.tsx* e non è possibile eseguire questa operazione, provare a usare l'istruzione in app.tsx o impostare punti di interruzione in `debugger;` Chrome Strumenti di sviluppo (o F12 Tools per Microsoft Edge). 

   * Se è necessario interrompere il codice in *app-bundle.js* e non è possibile eseguire questa operazione, rimuovere il file source map, *app-bundle.js.map*.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)
