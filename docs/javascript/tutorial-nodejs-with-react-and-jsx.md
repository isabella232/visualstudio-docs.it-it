---
title: Creare un'app Node.js e React
description: In questa esercitazione si creerà un'app usando Node.js Tools for Visual Studio
ms.custom: mvc
ms.date: 11/01/2018
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9259b5a813dc09389c57288e13eafd5a3adb0064
ms.sourcegitcommit: 5dc74b4fdff1357df43a19f6e8a51d7bf706abd6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2019
ms.locfileid: "55770570"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app React in Visual Studio

Visual Studio consente di creare con facilità un progetto Node.js e di provare IntelliSense e altre funzionalità incorporate che supportano Node.js. In questa esercitazione per Visual Studio si crea un progetto di applicazione web Node.js da un modello di Visual Studio. Quindi si crea un'app semplice usando React.

In questa esercitazione si imparerà a:
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

* È necessario che siano installati Visual Studio 2017 e il carico di lavoro di sviluppo Node.js.

    Se Visual Studio non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)  per installarlo gratuitamente.

    Se il carico di lavoro è già installato ed è necessario installare Visual Studio, selezionare il collegamento **Apri il programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo Node.js**, quindi scegliere **Modifica**.

* Il runtime di Node.js deve essere installato.

    Questa esercitazione è stata sottoposta a test con la versione 8.11.2.

    Se il runtime non è installato, installare la versione LTS dal sito Web [Node.js](https://nodejs.org/en/download/). In generale, Visual Studio rileva automaticamente il runtime di Node.js installato. Se non viene rilevato un runtime installato, è possibile usare la pagina delle proprietà per configurare il progetto in modo che faccia riferimento al runtime installato (dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Proprietà**).

## <a name="create-a-project"></a>Creare un progetto

Per prima cosa creare un progetto di applicazione Web Node.js.

1. Aprire Visual Studio 2017.

1. Sulla barra dei menu in alto scegliere **File** > **Nuovo** > **Progetto**.

1. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto** espandere **JavaScript** e quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, digitare il nome **NodejsWebAppBlank** e scegliere **OK**.

     Se non viene visualizzato il modello di progetto **Applicazione Web Node.js vuota** è necessario installare prima il carico di lavoro Sviluppo Node.js.

    Visual Studio crea la nuova soluzione e apre il progetto.

    ![Progetto Node.js in Esplora soluzioni](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo **Proprietà**. È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata su disco da un file con estensione *sln*, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json* è un file utilizzato da npm per gestire le dipendenze e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni su questo file, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md)

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

    Nella finestra di dialogo **Installa nuovi pacchetti npm** è possibile scegliere di installare la versione più recente dei pacchetti o specificare la versione desiderata. Se dopo aver scelto di installare la versione corrente di questi pacchetti si riscontrano errori imprevisti, potrebbe essere necessario installare le versioni esatte dei pacchetti citate più avanti in questa procedura.

1. Nella finestra di dialogo **Installa nuovi pacchetti npm** cercare il pacchetto react e selezionare **Installa pacchetto** per installarlo.

    ![Installa nuovi pacchetti npm](../javascript/media/tutorial-nodejs-react-install-packages.png)

    Selezionare la finestra **Output** per visualizzare lo stato di avanzamento dell'installazione del pacchetto (selezionare **Npm** nel campo **Mostra output di**). Dopo l'installazione il pacchetto viene visualizzato sotto il nodo **npm**.

    Il file *package.json* del progetto viene aggiornato con le nuove informazioni sul pacchetto, inclusa la versione del pacchetto.

1. Anziché usare l'interfaccia utente per cercare e aggiungere gli altri pacchetti uno alla volta, incollare il codice seguente nel file *package.json*. A tale scopo, aggiungere una sezione `dependencies` con il codice seguente:

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    Se la versione del modello vuoto in uso contiene già una sezione `dependencies`, sostituirla con il codice JSON precedente. Per altre informazioni sull'uso di questo file, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md)

1. Fare clic con il pulsante destro del mouse sul nodo **npm** nel progetto e scegliere **Aggiorna pacchetti npm**.

    Nel riquadro inferiore selezionare la finestra **Output** per vedere lo stato di avanzamento dell'installazione dei pacchetti. L'installazione potrebbe richiedere alcuni minuti e potrebbe non essere possibile visualizzare immediatamente i risultati. Per visualizzare l'output, assicurarsi di selezionare **Npm** nel campo **Mostra output di** della finestra **Output**.

    Ecco come appaiono i moduli npm in Esplora soluzioni dopo l'installazione.

    ![Pacchetti npm](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Se si preferisce installare pacchetti npm o comandi node.js dalla riga di comando, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**. Per installare i pacchetti, usare i comandi Node.js standard.

## <a name="add-project-files"></a>Aggiungere file di progetto

In questa procedura si aggiungono quattro nuovi file al progetto.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Per questa app semplice i nuovi file di progetto vengono aggiunti nella radice del progetto. Nella maggior parte delle app i file vengono aggiunti a sottocartelle e i riferimenti al percorso relativo vengono modificati di conseguenza.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto **NodejsWebAppBlank** e scegliere **Aggiungi** > **Nuovo elemento**.

1. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere **File JSX TypeScript**, digitare il nome *app.tsx* e selezionare **OK**.

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

    *app.tsx* è specificato come file di origine.

## <a name="transpile-the-jsx"></a>Eseguire il transpile di JSX

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Apri prompt dei comandi qui**.

1. Al prompt dei comandi digitare il seguente comando:

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    Il risultato viene visualizzato nella finestra del prompt dei comandi.

    ![Eseguire webpack](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    Se invece dell'output precedente vengono visualizzati degli errori, è necessario risolverli prima di poter eseguire l'app. Una causa degli errori può essere il fatto che le versioni dei pacchetti npm sono diverse da quelle visualizzate in questa esercitazione. Un modo per correggere gli errori consiste nell'usare le versioni esatte visualizzate nei passaggi precedenti. Se una o più di queste versioni dei pacchetti sono state deprecate e generano errori, potrebbe essere necessario installare una versione più recente per correggere gli errori. Per informazioni sull'uso di *package.json* per controllare le versioni del pacchetto npm, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md).

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi** > **Cartella esistente**, quindi scegliere la cartella *dist* e scegliere **Seleziona cartella**.

    Visual Studio aggiunge al progetto la cartella *dist* che contiene *app-bundle.js* e *app-bundle.js.map*.

1. Aprire *app-bundle.js* per visualizzare il codice JavaScript di cui è stato eseguito il transpile.

1. Se viene richiesto di ricaricare i file modificati esternamente, selezionare **Sì a tutti**.

    ![Caricare i file modificati](../javascript/media/tutorial-nodejs-react-reload-files.png)

Ogni volta che si apportano modifiche ad *app.tsx* è necessario eseguire nuovamente il comando webpack.

## <a name="run-the-app"></a>Eseguire l'app

1. Selezionare Chrome come destinazione di debug corrente.

    ![Selezionare Chrome come destinazione di debug](../javascript/media/tutorial-nodejs-react-debug-target.png)

    Se Chrome è disponibile nel computer in uso ma non viene visualizzato come opzione, scegliere **Esplora con** dall'elenco a discesa delle destinazioni di debug e selezionare Chrome come destinazione browser predefinita (scegliere **Imposta come predefinito**).

1. Per eseguire l'app, premere **F5** (**Debug** > **Avvia debug**) o fare clic sul pulsante con la freccia verde.

    Viene visualizzata una finestra della console Node.js che indica la porta sulla quale è in ascolto il debugger.

    Visual Studio avvia l'app eseguendo il file di avvio *server.js*.

    ![Eseguire React nel browser](../javascript/media/tutorial-nodejs-react-running-react.png)

1. Chiudere la finestra del browser.

1. Chiudere la finestra della console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Impostare un punto di interruzione ed eseguire l'app

1. In *server.js* fare clic nella barra a sinistra della dichiarazione `staticPath` per impostare un punto di interruzione:

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Per eseguire l'applicazione, premere **F5** (**Debug** > **Avvia debug**).

    Il debugger sospende l'esecuzione nel punto di interruzione impostato (l'istruzione corrente è contrassegnata in giallo). A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Premere **F5** per continuare con l'esecuzione dell'app.

1. Per usare Chrome Developer Tools, premere **F12**. È possibile usare questi strumenti per esaminare il modello DOM e interagire con l'app mediante la console JavaScript.

1. Chiudere il Web browser e la console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Impostare e raggiungere un punto di interruzione nel codice React lato client

Nella sezione precedente il debugger è stato associato al codice Node.js lato server. Per associare il debugger da Visual Studio e accedere a punti di interruzione nel codice React lato client, è necessario che il debugger identifichi il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

1. Chiudere tutte le finestre di Chrome.

2. Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`

    Viene avviato Chrome con il debug abilitato.

3. Passare a Visual Studio e impostare un punto di interruzione nel codice *app-bundle.js* in corrispondenza della funzione `render()`, come indicato di seguito:

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Per trovare la funzione `render()` in *app-bundle.js*, usare **CTRL**+**F** (**Modifica** > **Trova e sostituisci** > **Ricerca veloce**).

4. Con Chrome selezionato come destinazione di debug in Visual Studio, premere **CTRL**+**F5** (**Debug** > **Avvia senza eseguire debug**) per eseguire l'app nel browser.

    L'app viene aperta in una nuova scheda del browser.

5. Scegliere **Debug** > **Associa a processo**.

6. Nella finestra di dialogo **Associa a processo** scegliere **Webkit code** (Codice webkit) nel campo **Attach to** (Associa a), quindi digitare **chrome** nella casella del filtro per applicare un filtro ai risultati della ricerca.

7. Selezionare il processo di Chrome con la porta host corretta (in questo esempio 1337) e selezionare **Associa**.

    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili agli strumenti Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.

    > [!NOTE]
    > Se il debugger non è associato e viene visualizzato il messaggio "Impossibile connettersi al processo. Operazione non valida nello stato corrente." Usare Gestione attività per chiudere tutte le istanze di Chrome prima di avviare Chrome in modalità di debug. Se sono in esecuzione estensione di Chrome, la modalità di debug complete potrebbe essere impedita.

8. Dato che il codice con il punto di interruzione è già stato eseguito, aggiornare la pagina del browser per raggiungere il punto di interruzione.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**).

    A seconda dell'ambiente e dello stato del browser è possibile raggiungere il punto di interruzione in *app-bundle.js* o nel relativo percorso mappato in *app.tsx*. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

   * Se è necessario inserire un'interruzione nel codice in *app.tsx*, ma non è possibile eseguire questa operazione, usare **Associa a processo** come descritto nei passaggi precedenti per associare il debugger. A questo punto, aprire il file *app.tsx* generato dinamicamente da Esplora soluzioni selezionando **Documenti script** > **app.tsx**, impostare un punto di interruzione e aggiornare la pagina nel browser. Impostare il punto di interruzione in una riga di codice che ammetta i punti di interruzione, come l'istruzione `return` o una dichiarazione `var`.

       Oppure, se è necessario inserire un'interruzione nel codice in *app.tsx*, ma non è possibile eseguire questa operazione, provare a usare l'istruzione `debugger;` in *app.tsx* o impostare i punti di interruzione in Chrome Developer Tools.

   * Se è necessario inserire un'interruzione nel codice in *app bundle.js*, ma non è possibile eseguire questa operazione, rimuovere il file del mapping di origine *app-bundle.js.map*.

     > [!TIP]
     > Dopo aver eseguito per la prima volta l'associazione al processo seguendo questa procedura, è possibile ripetere rapidamente l'associazione allo stesso processo in Visual Studio 2017 scegliendo **Debug** > **Riassocia a processo**.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel Servizio app di Linux](../javascript/publish-nodejs-app-azure.md)