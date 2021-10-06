---
title: Creare un'app Node.js e React
description: Informazioni su come creare un Node.js di applicazione Web da un modello Visual Studio personalizzato.
ms.custom: vs-acquisition
ms.date: 09/14/2021
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
ms.openlocfilehash: 775e461afd78c88e004d09ce2561dad716d3c032
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2021
ms.locfileid: "129560958"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Esercitazione: Creare un progetto Node.js e un'app React in Visual Studio

Con Visual Studio, è possibile creare facilmente un progetto Node.js e usare IntelliSense e altre funzionalità incorporate che supportano Node.js. In questa esercitazione viene creato un progetto Node.js'app Web da un Visual Studio personalizzato. Quindi si crea un'app semplice usando React.

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un progetto Node.js
> * Aggiungere pacchetti npm
> * Aggiungere codice React all'app
> * Eseguire il transpile in JSX
> * Collegare il debugger

::: moniker range=">=vs-2022"
> [!IMPORTANT]
> A partire da Visual Studio 2022, è possibile creare un progetto [React](../javascript/tutorial-create-react-app.md) usando il nuovo tipo di progetto basato sull'interfaccia della riga [di comando](https://devblogs.microsoft.com/visualstudio/the-new-javascript-typescript-experience-in-vs-2022-preview-3/). Alcune delle informazioni contenute in questo articolo si applicano solo al Node.js di progetto predefinito (con estensione njsproj).
::: moniker-end

Prima di iniziare, ecco una rapida domanda frequente per presentare alcuni concetti chiave:

- **Che cos'è Node.js?**
  
  Node.js è un ambiente di runtime JavaScript lato server che esegue codice JavaScript.

- **Che cos'è npm?**
  
  La gestione pacchetti predefinita per Node.js è npm. Uno gestione pacchetti semplifica la pubblicazione e la condivisione di Node.js di codice sorgente. Gestione pacchetti npm semplifica l'installazione, l'aggiornamento e la disinstallazione della libreria.

- **Cos'è React?**
  
  React è un framework front-end per la creazione di un'interfaccia utente.

- **Cos'è JSX?**
  
  JSX è un'estensione della sintassi JavaScript usata in genere con React per descrivere gli elementi dell'interfaccia utente. È necessario eseguire il transpile del codice JSX in codice JavaScript normale prima di poterlo eseguire in un browser.

- **Cos'è webpack?**

  Webpack aggrega i file JavaScript in modo che possano essere eseguiti in un browser e può anche trasformare o creare il pacchetto di altre risorse e asset. Webpack può specificare un compilatore, ad esempio Babel o TypeScript, per eseguire il transpile di codice JSX o TypeScript in codice JavaScript normale.

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede i prerequisiti seguenti:

- Visual Studio con il carico di lavoro Node.js sviluppo di applicazioni installato.
  
  Se non è ancora stato installato Visual Studio:
  
  1. Passare alla pagina [Visual Studio download per](https://visualstudio.microsoft.com/downloads) installare Visual Studio gratuitamente.
     
  1. Nella finestra Programma di installazione di Visual Studio selezionare il carico di **lavoroNode.js sviluppo** e selezionare **Installa.**
     
     ![Screenshot che mostra il carico di lavoro Node js selezionato nel Programma di installazione di Visual Studio.](media/quickstart-nodejs-workload.png)
  
  Se è stato installato Visual Studio ma è necessario il carico Node.js carico di lavoro:
  
  1. In Visual Studio passare a **Strumenti**  >  **Ottieni strumenti e funzionalità.**
     
  1. Nella finestra Programma di installazione di Visual Studio scegliere il carico **di lavoroNode.js sviluppo** e selezionare Modifica per scaricare e installare il carico di lavoro. 
  
- Runtime Node.js installato:
  
  Se il runtime di Node.js non è installato, installare la versione [LTS](https://nodejs.org/en/download/)dal sito Web Node.js . La versione LTS offre la migliore compatibilità con altri framework e librerie.
  
  Gli Node.js nel carico di lavoro Visual Studio Node.js supportano sia le Node.js a 32 bit che a 64 bit. Visual Studio richiede una sola versione e il programma Node.js programma di installazione supporta solo una versione alla volta.
  
  Visual Studio in genere rileva automaticamente il runtime Node.js installato. In caso contrario, è possibile configurare il progetto per fare riferimento al runtime installato:
  
  1. Dopo aver creato un progetto, fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Proprietà.**
     
  1. Nel riquadro **Proprietà** impostare il percorsoNode.exe **per** fare riferimento a un'installazione globale o locale di Node.js. È possibile specificare il percorso di un interprete locale in ogni progetto Node.js progetto.

::: moniker range=">=vs-2022"
Questa esercitazione è stata testata con Node.js 14.17.5.
::: moniker-end
::: moniker range="<=vs-2019"
Questa esercitazione è stata testata con Node.js 12.6.2.
::: moniker-end

## <a name="create-a-project"></a>Creare un progetto

Creare prima di tutto un Node.js di app Web.

::: moniker range=">=vs-2022"
1. Aprire Visual Studio e premere **ESC** per chiudere la finestra iniziale.
   
1. Premere **CTRL** Q, digitarenode.jsnella casella di ricerca e quindi scegliere Blank + Node.js Web Application - **JavaScript (Applicazione Web vuota - JavaScript)** dall'elenco a discesa. 
   
   Anche se questa esercitazione usa il compilatore TypeScript, i passaggi richiedono di iniziare con il **modello JavaScript.**
   
   Se non viene visualizzata la scelta Blank **Node.js Web Application** (Applicazione Web vuota), è necessario installare il carico di Node.js di sviluppo. Per istruzioni, vedere [Prerequisiti.](#prerequisites)
   
1. Nella finestra **di dialogo Configura il nuovo** progetto selezionare **Crea.**
   
   Visual Studio crea la nuova soluzione e il nuovo progetto e apre il progetto nel riquadro destro. Il *server.js* file di progetto verrà aperto nell'editor nel riquadro sinistro.
   
1. Esaminare la struttura del progetto **Esplora soluzioni** nel riquadro destro.
   
   ![Screenshot che mostra la Node.js del progetto in Esplora soluzioni.](media/vs-2022/tutorial-nodejs-react-project-structure.png)
   
   - Al livello superiore è disponibile la *soluzione* (**1**), che per impostazione predefinita ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.
   
   - Il progetto (**2**), usando il nome specificato nella finestra di dialogo Configura il **nuovo progetto,** è evidenziato in grassetto. Nell'file system il progetto è un file con estensione *njsproj* nella cartella del progetto.
     
     Per visualizzare e impostare le proprietà del progetto e le variabili di ambiente, premere **ALT INVIO** oppure fare clic con il pulsante destro del mouse sul progetto e +  **scegliere Proprietà** dal menu di scelta rapida. È possibile usare altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine Node.js progetto.
   
   - Il **nodo npm** (**3**) mostra tutti i pacchetti npm installati.
   
     Fare clic con il pulsante destro del mouse sul **nodo npm** per cercare e installare i pacchetti npm. È possibile installare e aggiornare i pacchetti usando le impostazioni in *package.json* e le opzioni di clic con il pulsante destro del mouse nel **nodo npm.**
   
   - Npm usa il file *package.json* (**4**) per gestire le dipendenze e le versioni per i pacchetti installati in locale. Per altre informazioni, vedere [Gestire i pacchetti npm.](npm-package-management.md)
   
   - Project file (**5**) vengono visualizzati sotto il nodo del progetto. Il file di avvio del *progetto,server.js*, viene visualizzato in grassetto.
     
     Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.
::: moniker-end
::: moniker range="vs-2019"
1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    Premere **ESC** per chiudere la finestra iniziale. Premere **CTRL+Q** per aprire la casella di ricerca, **digitareNode.js** e quindi scegliere Blank Node.js Web Application - JavaScript (Applicazione Web vuota - **JavaScript).** Anche se questa esercitazione usa il compilatore TypeScript, i passaggi richiedono di iniziare con il **modello JavaScript.**
    
    Nella finestra di dialogo visualizzata scegliere **Crea**.

    Se il modello di progetto Applicazione **Web Node.js** vuoto non è visualizzato, è necessario aggiungere il carico diNode.js **di sviluppo.** Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto.

    ![Screenshot che mostra il progetto Node.js in Esplora soluzioni](media/tutorial-nodejs-react-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo Proprietà **(o** **premendo ALT**  +  **INVIO).** È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json è* un file usato da npm per gestire le dipendenze dei pacchetti e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm.](../javascript/npm-package-management.md)

    (5) I file di progetto come *server.js* vengono visualizzati sotto il nodo del progetto. *server.js* è il file di avvio del progetto e per questo motivo viene visualizzato in **grassetto**. Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.
::: moniker-end
::: moniker range="vs-2017"
1. Aprire Visual Studio.

1. Creare un nuovo progetto.

    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro di sinistra della finestra di dialogo **Nuovo progetto** espandere **JavaScript**, quindi selezionare **Node.js**. Nel riquadro centrale scegliere **Applicazione Web Node.js vuota**, digitare il nome **NodejsWebAppBlank**, quindi scegliere **OK**.

    Se il modello di progetto Applicazione **Web Node.js** vuoto non è visualizzato, è necessario aggiungere il carico diNode.js **di sviluppo.** Per istruzioni dettagliate, vedere i [Prerequisiti](#prerequisites).

    Visual Studio crea la nuova soluzione e apre il progetto.

    ![Screenshot che mostra il progetto Node.js in Esplora soluzioni](media/tutorial-nodejs-react-project-structure.png)

    (1) Il progetto viene visualizzato in **grassetto**, con il nome assegnato in precedenza nella finestra di dialogo **Nuovo progetto**. Nel file system il progetto è rappresentato da un file con estensione *njsproj* nella cartella del progetto. È possibile impostare le proprietà e le variabili di ambiente associate al progetto facendo clic con il pulsante destro del mouse sul progetto e scegliendo Proprietà **(o** **premendo ALT**  +  **INVIO).** È possibile eseguire sequenze di andata e ritorno con altri strumenti di sviluppo, perché il file di progetto non apporta modifiche personalizzate all'origine del progetto Node.js.

    (2) Al primo livello è presente una soluzione che, per impostazione predefinita, ha lo stesso nome del progetto. Una soluzione, rappresentata da un file *con estensione sln* su disco, è un contenitore per uno o più progetti correlati.

    (3) Il nodo npm visualizza tutti i pacchetti npm eventualmente installati. È possibile fare clic con il pulsante destro del mouse sul nodo npm per cercare e installare i pacchetti npm utilizzando una finestra di dialogo o per installare e aggiornare i pacchetti usando le impostazioni in *package.json* e fare clic con il pulsante destro del mouse sulle opzioni nel nodo npm.

    (4) *package.json è* un file usato da npm per gestire le dipendenze dei pacchetti e le versioni dei pacchetti per i pacchetti installati localmente. Per altre informazioni, vedere [Gestire i pacchetti npm.](../javascript/npm-package-management.md)

    (5) I file di progetto come *server.js* vengono visualizzati sotto il nodo del progetto. *server.js* è il file di avvio del progetto e per questo motivo viene visualizzato in **grassetto**. Impostare il file di avvio facendo clic con il pulsante destro del mouse su un file del progetto e selezionando **Imposta come file di avvio Node.js**.
::: moniker-end

## <a name="add-npm-packages"></a>Aggiungere pacchetti npm

Per l'esecuzione corretta di questa app sono necessari i moduli npm seguenti:

- react
- react-dom
- express
- path
- ts-loader
- typescript
- webpack
- webpack-cli

Per installare un pacchetto:

1. In **Esplora soluzioni** fare clic con il pulsante destro del **mouse sul nodo npm** e **scegliere Install New npm Packages (Installa nuovi pacchetti npm).**
   
1. Nella finestra di dialogo Install New npm Packages (Installa nuovi pacchetti **npm)** cercare il **pacchetto react** e selezionare Install **Package (Installa** pacchetto) per installarlo.

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra l'installazione di un pacchetto npm.](media/vs-2022/tutorial-nodejs-react-install-package.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra l'installazione di un pacchetto npm.](media/tutorial-nodejs-react-install-package.png)
    ::: moniker-end

    Nella finestra di dialogo Installa nuovi **pacchetti npm** è possibile scegliere di installare la versione più recente del pacchetto o di specificare una versione. Se si sceglie di installare le versioni correnti, ma si verificano errori imprevisti in un secondo momento, provare a installare le versioni esatte del pacchetto elencate nel passaggio successivo.

    La **finestra Output** nel riquadro inferiore Visual Studio mostra lo stato di avanzamento dell'installazione del pacchetto. Aprire la **finestra Output** selezionando **Visualizza**  >  **output** o premendo **CTRL** +  + **ALT+O.** Nel campo **Mostra output** da della finestra **Output** selezionare **Npm**.

    Quando è installato, il **pacchetto react** viene visualizzato sotto il **nodo npm** in **Esplora soluzioni**.
    
    Il file *package.json del progetto* viene aggiornato con le nuove informazioni sul pacchetto, inclusa la versione del pacchetto.

Invece di usare l'interfaccia utente per cercare e aggiungere il resto dei pacchetti uno alla volta, è possibile incollare il codice del pacchetto necessario in *package.json.*
    
1. Da **Esplora soluzioni** aprire **package.json** nell'editor Visual Studio. Aggiungere la sezione `dependencies` seguente prima della fine del file:

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

    Se il file contiene già `dependencies` una sezione , sostituirla con il codice JSON precedente. Per altre informazioni sull'uso del file *package.json,* vedere [configurazione di package.json.](configure-packages-with-package-json.md)

1. Premere **CTRL** + **S** o selezionare **File**  >  **Salva package.json** per salvare le modifiche.

1. In **Esplora soluzioni** fare clic con il pulsante destro **del mouse sul nodo npm** nel progetto e **scegliere Installa pacchetti npm**.

    Questo comando esegue direttamente il comando npm install per installare tutti i pacchetti elencati in *packages.json.*

    Selezionare la finestra **Output** nel riquadro inferiore per visualizzare lo stato dell'installazione. L'installazione potrebbe richiedere alcuni minuti e i risultati potrebbero non essere visualizzati immediatamente. Assicurarsi di selezionare **Npm** nel campo **Mostra output da** nella finestra **Output.**

    Dopo l'installazione, i moduli npm vengono visualizzati nel **nodo npm** in **Esplora soluzioni**.

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra i pacchetti npm installati.](media/vs-2022/tutorial-nodejs-react-npm-modules-installed.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra i pacchetti npm installati.](media/tutorial-nodejs-react-npm-modules-installed.png)
    ::: moniker-end

    > [!NOTE]
    > È anche possibile installare pacchetti npm tramite la riga di comando. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto e **scegliere Apri prompt dei comandi qui.** Per installare i pacchetti, usare i comandi Node.js standard.

## <a name="add-project-files"></a>Aggiungere file di progetto

Aggiungere quindi quattro nuovi file al progetto.

- *app.tsx*
- *webpack-config.js*
- *index.html*
- *tsconfig.json*

Per questa app semplice i nuovi file di progetto vengono aggiunti nella radice del progetto. Per la maggior parte delle app, si aggiungono i file alle sottocartelle e si modificano di conseguenza i riferimenti al percorso relativo.

1. In **Esplora soluzioni** selezionare il nome del progetto e premere **CTRL** MAIUSC A oppure fare clic con il pulsante destro del mouse sul nome del progetto +  + e **scegliere Aggiungi** nuovo  >  **elemento.**

1. Nella finestra **di dialogo Aggiungi nuovo** elemento scegliere File **JSX TypeScript,** digitare il nome *app.tsx* e selezionare **Aggiungi** o **OK.**

1. Ripetere questi passaggi per aggiungere un **file JavaScript** denominato *webpack-config.js*.

1. Ripetere questi passaggi per aggiungere un **file HTML** *denominatoindex.html*.

1. Ripetere questi passaggi per aggiungere un **file di configurazione JSON TypeScript** denominato *tsconfig.json.*

## <a name="add-app-code"></a>Aggiungere il codice dell'app

1. In **Esplora soluzioni** aprire **server.js** e sostituire il codice esistente con il codice seguente:

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

   Il codice precedente usa Express per avviare Node.js come server di applicazioni web. Il codice imposta la porta sul numero di porta configurato nelle proprietà del progetto, che per impostazione predefinita è 1337. Se è necessario aprire le proprietà del progetto, fare clic con il pulsante destro del mouse sul nome del **progetto** Esplora soluzioni e **scegliere Proprietà**.

1. Aprire **app.tsx** e aggiungere il codice seguente:

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

    Il codice precedente usa la sintassi JSX React per visualizzare un messaggio.

1. Aprire **index.html** e sostituire la `body` sezione con il codice seguente:

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Questa pagina HTML carica *app-bundle.js*, che contiene il codice JSX e React convertito tramite transpile in codice JavaScript semplice. Attualmente *app-bundle.js* è un file vuoto. Nella sezione successiva, si configurano le opzioni per eseguire il transpile del codice.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configurare le opzioni di webpack e del compilatore TypeScript

Aggiungere quindi il codice di configurazione webpack *webpack-config.js*. Si aggiunge una semplice configurazione webpack che specifica un file di input, *app.tsx,* e un file di output, *app-bundle.js*, per la creazione di aggregazioni e il transpiling di JSX in codice JavaScript normale. Per l'esecuzione del transpile si configurano anche alcune opzioni del compilatore TypeScript. Questo codice di configurazione di base è un'introduzione a webpack e al compilatore TypeScript.

1. In **Esplora soluzioni** aprire **webpack-config.js** e aggiungere il codice seguente.

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

1. Aprire **tsconfig.json e** sostituire il contenuto con il codice seguente, che specifica le opzioni del compilatore TypeScript:

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

    Il codice specifica *app.tsx* come file di origine.

1. Premere  + **CTRL+MAIUSC** + **S** o selezionare **File**  >  **Salva tutto** per salvare tutte le modifiche.

## <a name="transpile-the-jsx"></a>Eseguire il transpile di JSX

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto e **scegliere Apri prompt dei comandi qui.**

1. Al prompt dei comandi immettere il comando webpack seguente:

    `node_modules\.bin\webpack ./app.tsx --config webpack-config.js`

    Il risultato viene visualizzato nella finestra del prompt dei comandi.

    ![Screenshot che mostra i risultati dell'esecuzione del comando webpack.](media/tutorial-nodejs-react-run-webpack-cmd.png)

    Se invece dell'output precedente vengono visualizzati degli errori, è necessario risolverli prima di poter eseguire l'app. Se le versioni del pacchetto npm sono diverse da quelle specificate in questa esercitazione, ciò può causare errori. Un modo per correggere gli errori consiste nell'usare le versioni esatte illustrate nel passaggio precedente.
    
    Inoltre, se una o più versioni del pacchetto sono deprecate e causano un errore, potrebbe essere necessario installare una versione più recente per correggere gli errori. Per informazioni sull'uso di *package.json* per controllare le versioni del pacchetto npm, vedere [Configurazione di package.json](../javascript/configure-packages-with-package-json.md).

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** cartella  >  **esistente.**

1. Selezionare la *cartella dist* e quindi selezionare **Seleziona cartella.**

    Visual Studio aggiunge la *cartella dist,* che contiene *app-bundle.js* *eapp-bundle.js.map,* al progetto.

1. Aprire *app-bundle.js* per visualizzare il codice JavaScript di cui è stato eseguito il transpile.

1. Se viene richiesto se ricaricare i file modificati esternamente, selezionare **Sì a tutti.**

    ![Screenshot che mostra un prompt che indica se caricare i file modificati.](media/tutorial-nodejs-react-reload-files.png)

Ogni volta che si apportano modifiche *a app.tsx,* è necessario eseguire di nuovo il comando webpack. Per automatizzare questo passaggio, è possibile aggiungere uno script di compilazione per eseguire il transpile di JSX.

### <a name="add-a-build-script-to-transpile-the-jsx"></a>Aggiungere uno script di compilazione per il transpile di JSX

Visual Studio versioni precedenti a Visual Studio 2019 richiedono uno script di compilazione. Invece di eseguire il transpile di JSX dalla riga di comando, come illustrato nella sezione precedente, è possibile eseguire il transpile di JSX durante la compilazione da Visual Studio.

1. Aprire *package.json* e aggiungere la sezione seguente dopo la sezione `dependencies`:

   ```json
   "scripts": {
    "build": "webpack-cli ./app.tsx --config webpack-config.js"
   }
   ```

1. Salvare le modifiche.

## <a name="run-the-app"></a>Eseguire l'app

1. Nella barra **degli strumenti Debug** selezionare Server Web **(Microsoft Edge)** o **Server Web (Google Chrome)** come destinazione di debug.

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra la selezione Microsoft Edge come destinazione di debug.](media/vs-2022/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="=vs-2019"
    ![Screenshot che mostra la selezione di Chrome come destinazione di debug.](media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Screenshot che mostra la selezione di Chrome come destinazione di debug.](media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    Se si sa che la destinazione di debug preferita è disponibile nel computer, ma non viene visualizzata come opzione, selezionare **Sfoglia** con nell'elenco a discesa della destinazione di debug. Selezionare la destinazione del browser predefinita nell'elenco e selezionare **Imposta come predefinita.**

1. Per eseguire l'app, premere **F5,** selezionare il pulsante freccia verde o selezionare **Debug**  >  **Avvia debug.**

    Verrà Node.js finestra della console che mostra la porta di ascolto del debugger.

    Visual Studio avvia l'app eseguendo il file di avvio *server.js*.

    ![Screenshot che mostra l'React in un browser.](media/tutorial-nodejs-react-running-react.png)

1. Chiudere le finestre del browser e della console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Impostare un punto di interruzione ed eseguire l'app

I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica dove Visual Studio deve sospendere il codice in esecuzione. È quindi possibile osservare i valori delle variabili, il comportamento della memoria o se un ramo di codice è in esecuzione.

1. In *server.js* fare clic nella barra a sinistra della dichiarazione `staticPath` per impostare un punto di interruzione:

    ::: moniker range=">=vs-2022"
    ![Screenshot che mostra un punto di interruzione impostato per la dichiarazione staticPath nel server dot j s.](media/vs-2022/tutorial-nodejs-react-set-breakpoint.png)
    ::: moniker-end
    ::: moniker range="<=vs-2019"
    ![Screenshot che mostra un punto di interruzione impostato per la dichiarazione staticPath nel server dot j s.](media/tutorial-nodejs-react-set-breakpoint.png)
    ::: moniker-end

1. Per eseguire l'app, premere **F5** o selezionare **Debug**  >  **Avvia debug**.

    Il debugger viene sospeso in corrispondenza del punto di interruzione impostato, con l'istruzione corrente evidenziata. A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Per continuare a eseguire l'app, premere **F5,** selezionare **Continua** nella barra degli strumenti **Debug** o selezionare **Debug**  >  **Continua.**

   Se si vuole usare Chrome Strumenti di sviluppo o F12 Tools for Microsoft Edge, premere **F12**. È possibile usare questi strumenti per esaminare il DOM e interagire con l'app usando la console JavaScript.

1. Chiudere le finestre del browser e della console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Impostare e raggiungere un punto di interruzione nel codice React lato client

Nella sezione precedente il debugger è stato associato al codice Node.js lato server. Per connettersi e trovare punti di interruzione nel codice React lato client, è necessario collegare il debugger al processo corretto. Ecco un modo per abilitare un browser e collegare un processo per il debug.

### <a name="enable-the-browser-for-debugging"></a>Abilitare il browser per il debug

::: moniker range=">=vs-2019"
È possibile usare Microsoft Edge o Google Chrome. Chiudere tutte le finestre per il browser di destinazione. Ad Microsoft Edge, arrestare anche tutte le istanze di Chrome. Poiché entrambi i browser condividono la Chromium base di codice, l'arresto di entrambi i browser offre i risultati migliori.

Altre istanze del browser possono impedire l'apertura del browser con il debug abilitato. Le estensioni del browser potrebbero impedire la modalità di debug completo. Potrebbe essere necessario usare le Gestione attività per trovare e terminare tutte le istanze di Chrome in esecuzione.

Per avviare il browser con il debug abilitato:

1. Selezionare **Sfoglia con dall'elenco** a discesa nella barra degli **strumenti Debug.** 
   
1. Nella schermata **Sfoglia con,** con il browser preferito evidenziato, selezionare **Aggiungi**.
   
1. Immettere il flag *--remote-debugging-port=9222* nel **campo** Argomenti.
   
1. Assegnare al browser un nuovo nome descrittivo, ad esempio *Edge with debugging (Edge con* debug) o Chrome with debugging *(Chrome con debug)* e quindi selezionare **OK.**
   
1. Nella schermata **Sfoglia** con selezionare **Sfoglia**.

    ![Screenshot che mostra la creazione di un browser Edge con il debug abilitato.](media/tutorial-nodejs-react-edge-with-debugging.png)

- In alternativa, è possibile aprire il **comando Esegui** facendo clic con il pulsante destro del mouse Windows **pulsante Start** e immettere:
  
  `msedge --remote-debugging-port=9222`
  
  oppure
  
  `chrome.exe --remote-debugging-port=9222`
::: moniker-end

::: moniker range="vs-2017"
Per questo scenario, usare Chrome.

1. Chiudere tutte le finestre del browser Chrome.

   Altre istanze del browser possono impedire l'apertura del browser con il debug abilitato. Le estensioni del browser potrebbero impedire la modalità di debug completo. Potrebbe essere necessario aprire il Gestione attività per trovare tutte le istanze di Chrome in esecuzione.

2. Avviare il browser con il debug abilitato.

    Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`
::: moniker-end

Il browser viene avviato con il debug abilitato. L'app non è ancora in esecuzione, quindi la pagina del browser è vuota.

### <a name="attach-the-debugger-to-client-side-script"></a>Collegare il debugger allo script lato client

1. Nell'editor Visual Studio impostare un punto di interruzione nel *codice sorgenteapp-bundle.js* *o app.tsx.*

    - Per *app-bundle.js*, impostare il punto di interruzione nella `render()` funzione . Per trovare la funzione nel fileapp-bundle.js, premere CTRL F o selezionare Modifica Ricerca e sostituisci Ricerca veloce e immettere `render()`   +    >    >   *render* nel campo di ricerca.

      ::: moniker range=">=vs-2022"
      ![Screenshot che mostra un punto di interruzione impostato nella funzione di rendering in app-bundle dot j s.](media/vs-2022/tutorial-nodejs-react-set-breakpoint-client-code.png)
      ::: moniker-end
      ::: moniker range="<=vs-2019"
      ![Screenshot che mostra un punto di interruzione impostato nella funzione di rendering in app-bundle dot j s.](media/tutorial-nodejs-react-set-breakpoint-client-code.png)
      ::: moniker-end

    - Per *app.tsx*, impostare il punto di interruzione all'interno `render()` della funzione nell'istruzione `return` .

      ::: moniker range=">=vs-2022"
      ![Screenshot che mostra un punto di interruzione impostato sull'istruzione return della funzione di rendering nell'app dot t s x.](media/vs-2022/tutorial-nodejs-react-set-breakpoint-tsx-file.png)
      ::: moniker-end
      ::: moniker range="<=vs-2019"
      ![Screenshot che mostra un punto di interruzione impostato sull'istruzione return della funzione di rendering nell'app dot t s x.](media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)
      ::: moniker-end

      Se si imposta il punto di interruzione  in *app.tsx,* aggiornare anchewebpack-config.jsper sostituire il codice seguente e salvare le modifiche.

      Sostituire questo codice:

      ```javascript
      output: {
          filename: "./app-bundle.js",
      },
      ```

      Con questo codice:

      ```javascript
      output: {
          filename: "./app-bundle.js",
          devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
      },
      ```

      Questa impostazione di solo sviluppo abilita il debug in Visual Studio. Per impostazione predefinita, i riferimenti webpack nel file source map includono il prefisso *webpack:///,* che impedisce Visual Studio trovare il file di origine *app.tsx.* Questa impostazione sostituisce i riferimenti generati nel file source map, *app-bundle.js.map,* durante la compilazione dell'app. In particolare, questa impostazione modifica il riferimento al file di origine *da webpack:///./app.tsx* a *./app.tsx,* che abilita il debug.

1. Selezionare il browser di destinazione come destinazione di debug in Visual Studio e quindi premere **CTRL** F5 oppure selezionare Debug Avvia senza eseguire debug per eseguire l'app +    >  nel browser.

    ::: moniker range=">=vs-2019"
    Se è stata creata una configurazione del browser abilitata per il debug con un nome descrittivo, scegliere tale browser come destinazione di debug.
    ::: moniker-end

    L'app viene aperta in una nuova scheda del browser.

1. Selezionare **Debug**  >  **Attach to Process (Esegui** debug connessione a processo) o premere **CTRL** +  + **ALT+P.**

    > [!TIP]
    > Dopo la prima connessione al processo, è possibile ricollegare rapidamente lo stesso processo selezionando **Debug** Ricollegare a processo o premendo  >   **MAIUSC** + **ALT** + **P.**

1. Nella finestra **di dialogo Associa a** processo ottenere un elenco filtrato di istanze del browser a cui è possibile connettersi.

    ::: moniker range=">=vs-2019"
    Assicurarsi che nel campo Collega a sia visualizzato il debugger corretto per il browser di destinazione,  **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium).** Digitare *chrome* o *edge* nella casella del filtro per filtrare i risultati.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **Webkit code (Codice Webkit)** **nel campo Attach to (Collega a).** Digitare **chrome nella** casella del filtro per filtrare i risultati della ricerca.
    ::: moniker-end

1. Selezionare il processo del browser con la porta host corretta, **localhost** in questo esempio. Nel campo Titolo potrebbe essere visualizzato anche il  numero di porta **1337** o **localhost** per selezionare il processo corretto.

1. Selezionare **Allega**.

    ::: moniker range=">=vs-2019"
    L'esempio seguente mostra **una finestra Associa a** processo per Microsoft Edge browser.

    ![Screenshot che mostra la finestra di dialogo Associa a processo.](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Screenshot che mostra la finestra di dialogo Associa a processo.](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Quando il debugger si collega correttamente, il DOM Explorer e la console JavaScript si aprono in Visual Studio. Questi strumenti di debug sono simili ai Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se il debugger non si collega e viene visualizzato il messaggio **Impossibile connettersi al processo. Un'operazione non è valida nello** stato corrente. , usare Gestione attività per chiudere tutte le istanze del browser di destinazione prima di avviare il browser in modalità di debug. Le estensioni del browser potrebbero essere in esecuzione e impedire la modalità di debug completo.

1. Dato che il codice con il punto di interruzione è già stato eseguito, aggiornare la pagina del browser per raggiungere il punto di interruzione.

    A seconda dell'ambiente, dello stato del browser e dei passaggi seguiti in precedenza, è possibile che venga raggiunto il punto di interruzione in *app-bundle.js* o nella relativa posizione mappata in *app.tsx.* In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

    Mentre il debugger è in pausa, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. Per eseguire il codice istruzione per istruzione, premere **F11** o selezionare **Esegui debug**  >  **istruzione oppure** premere **F10** o selezionare **Esegui debug**  >  **istruzione/istruzione.** Per continuare l'esecuzione del codice, **premere F5** o selezionare **Continua.** Per altre informazioni sulle funzionalità di debug di base, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

   - Se non è possibile interrompere il codice in *app.tsx,* riprovare a usare **Associa** a processo per collegare il debugger come descritto nei passaggi precedenti. Assicurarsi che l'ambiente sia configurato correttamente:

      - Chiudere tutte le istanze del browser, incluse le estensioni di Chrome, usando il Gestione attività. Assicurarsi di avviare il browser in modalità di debug.

      - Assicurarsi che il file source map includa un riferimento a *./app.tsx* e non *webpack:///./app.tsx*, impedendo così al debugger di Visual Studio di individuare *app.tsx.*

     In alternativa, provare a usare l'istruzione `debugger;` in *app.tsx* o impostare punti di interruzione nel Strumenti di sviluppo Chrome o in F12 Tools per Microsoft Edge.

   - Se non è possibile interrompere il codice in *app-bundle.js*, rimuovere il file source map, *app-bundle.js.map*.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Distribuire l'app nel servizio app di Linux](../javascript/publish-nodejs-app-azure.md)
