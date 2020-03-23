---
title: Eseguire il debug di un'app JavaScript o TypeScript
description: Visual Studio offre supporto per il debug di app JavaScript e TypeScript in Visual Studio
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678974"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Eseguire il debug di un'app JavaScript o TypeScript in Visual Studio

È possibile eseguire il debug di codice JavaScript e TypeScript con Visual Studio. È possibile impostare e raggiungere punti di interruzione, collegare il debugger, esaminare variabili, visualizzare lo stack di chiamate e usare altre funzionalità di debug.

> [!TIP]
> Se Visual Studio non è già stato installato, passare alla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente. A seconda del tipo di sviluppo di app che si sta eseguendo, può essere necessario installare il **carico di lavoro Sviluppo Node.js** con Visual Studio.

## <a name="debug-server-side-script"></a>Eseguire il debug di script lato server

1. Con il progetto aperto in Visual Studio, aprire un file JavaScript lato server (ad esempio *server.js*) e fare clic nella barra di navigazione sinistra per impostare un punto di interruzione:

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Per eseguire l'app premere **F5** (**Debug** > **Avvia debug**).

    Il debugger sospende l'esecuzione nel punto di interruzione impostato (l'istruzione corrente è contrassegnata in giallo). A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Premere **F5** per continuare con l'esecuzione dell'app.

1. Per usare Chrome Developer Tools o gli Strumenti F12, premere **F12**. È possibile usare questi strumenti per esaminare il modello DOM e interagire con l'app mediante la console JavaScript.

## <a name="debug-client-side-script"></a>Debug di script lato client

::: moniker range=">=vs-2019"
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e Microsoft Edge (Chromium). In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script sul lato client nelle app ASP.NET, vedere il post di blog [Debug JavaScript in Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) e questo post per Google [Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Per il debug di TypeScript in ASP.NET Core, consultate anche [Creare un'app ASP.NET Core con TypeScript.](tutorial-aspnet-with-typescript.md)
::: moniker-end
::: moniker range="vs-2017"
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e Internet Explorer. In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script sul lato client nelle app ASP.NET, consultate il post di blog [Debug lato client di progetti ASP.NET in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Per applicazioni diverse da ASP.NET, seguire i passaggi descritti di seguito.

### <a name="prepare-your-app-for-debugging"></a>Preparare l'app per il debugPrepare your app for debugging

Se l'origine è minimizzata o creata da un transpiler come TypeScript o Babel, è necessario usare [mapping di origine](#generate_source_maps) per ottenere la migliore esperienza di debug. Senza i mapping di origine, è comunque possibile collegare il debugger a uno script lato client in esecuzione. Tuttavia in molti casi è possibile impostare e raggiungere punti di interruzione solo nel file minimizzato o convertito tramite transpiler, e non nel file di origine. Ad esempio, in un'app Vue.js lo script minimizzato viene passato come stringa a un'istruzione `eval` e l'esecuzione efficace del codice istruzione per istruzione con il debugger di Visual Studio è possibile solo se si usano i mapping di origine. In scenari di debug complessi, è anche possibile utilizzare Chrome Developer Tools o F12 Tools per Microsoft Edge.

Per informazioni sulla generazione di mappe di origine, vedere Generare mappe di [origine per il debug.](#generate_source_maps)

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>Preparare il browser per il debug

::: moniker range=">=vs-2019"
Per questo scenario, utilizzare Microsoft Edge (Chromium), attualmente denominato **Microsoft Edge Beta** nell'IDE o Chrome.
::: moniker-end
::: moniker range="vs-2017"
Per questo scenario, utilizzare Chrome.
::: moniker-end

1. Chiudere tutte le finestre per il browser di destinazione.

   Altre istanze del browser possono impedire l'apertura del browser con il debug abilitato. (Estensioni del browser potrebbero essere in esecuzione e impedendo la modalità di debug completo, quindi potrebbe essere necessario aprire Task Manager per trovare istanze impreviste di Chrome.)

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (Chromium), arrestare anche tutte le istanze di Chrome. Poiché entrambi i browser utilizzano la base di codice cromo, questo dà i migliori risultati.
   ::: moniker-end

2. Avviare il browser con il debug abilitato.

    ::: moniker range=">=vs-2019"
    A partire da Visual Studio 2019, è possibile `--remote-debugging-port=9222` impostare il flag all'avvio del browser selezionando Sfoglia **con...** > dalla barra degli strumenti **Debug,** quindi scegliendo **Aggiungi**, quindi impostando il flag nel campo **Argomenti.** Utilizzare un nome descrittivo diverso per il browser, ad esempio **Edge with Debugging** o Chrome con **Debugging**. Per informazioni dettagliate, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-v16.2).

    ![Impostare il browser per l'apertura con il debug abilitato](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    In alternativa, aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**), quindi immettere il comando seguente:

    `msedge --remote-debugging-port=9222`

    o

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Verrà avviato il browser con il debug abilitato.

    L'app non è ancora in esecuzione, quindi ottieni una pagina vuota del browser.

### <a name="attach-the-debugger-to-client-side-script"></a>Connettere il debugger allo script sul lato client

Per connettere il debugger da Visual Studio e raggiungere i punti di interruzione nel codice lato client, il debugger ha bisogno di aiuto per identificare il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

1. Passare a Visual Studio e quindi impostare un punto di interruzione nel codice sorgente, che potrebbe essere un file JavaScript, un file TypeScript o un file JSX. Impostare il punto di interruzione in una riga di codice che consenta i punti di interruzione, ad esempio un'istruzione return o una dichiarazione var.

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Per trovare il codice specifico in un file transaccumulato, utilizzare **Ctrl**+**F** (**Modifica** > **ricerca e sostituzione** > **ricerca rapida**).

    Per il codice lato client, per raggiungere un punto di interruzione in un file TypeScript, in un file *con estensione vue*o JSX è in genere necessario utilizzare mappe di [origine.](#generate_source_maps) Una mappa di origine deve essere configurata correttamente per supportare il debug in Visual Studio.A source map must be configured correctly to support debugging in Visual Studio.

2. Selezionare il browser di destinazione come destinazione di debug in Visual Studio, quindi premere **CTRL**+**F5** (**Avvio debug** > **senza eseguire debug**) per eseguire l'app nel browser.

    ::: moniker range=">=vs-2019"
    Se è stata creata una configurazione del browser con un nome descrittivo, sceglierlo come destinazione di debug.
    ::: moniker-end

    L'app viene aperta in una nuova scheda del browser.

3. Scegliere **Esegui debug** > **connessione da elaborare**.

    > [!TIP]
    > A partire da Visual Studio 2017, una volta che ci si connette al processo per la prima volta seguendo questi passaggi, è possibile ricollegarsi rapidamente allo stesso processo scegliendo**Ricollega al processo**di **debug.** > 

4. Nella finestra di dialogo **Connetti a processo** ottenere un elenco filtrato di istanze del browser a cui è possibile connettersi.
    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere il debugger corretto per il browser di destinazione, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** nel campo **Allega a,** digitare **chrome** o **edge** nella casella del filtro per filtrare i risultati della ricerca.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **Codice Webkit** nel campo **Allega a,** digitare **chrome** nella casella del filtro per filtrare i risultati della ricerca.
    ::: moniker-end

5. Selezionare il processo del browser con la porta host corretta (localhost in questo esempio) e selezionare **Attach**.

    La porta (ad esempio, 1337) può essere visualizzata anche nel campo **Titolo** per facilitare la selezione dell'istanza corretta del browser.

    ::: moniker range=">=vs-2019"
    Nell'esempio seguente viene illustrato l'aspetto del browser Microsoft Edge (Chromium).

    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili ai Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se il debugger non si connette e viene visualizzato il messaggio "Impossibile avviare l'adapter di debug" o "Impossibile connettersi al processo. Un'operazione non è valida nello stato corrente.", utilizzare Task Manager di Windows per chiudere tutte le istanze del browser di destinazione prima di avviare il browser in modalità di debug. Le estensioni del browser potrebbero essere in esecuzione e impedire la modalità di debug completo.

6. Poiché il codice con il punto di interruzione potrebbe essere già stato eseguito, aggiornare la pagina del browser. Se necessario, eseguire un'azione per fare in modo che il codice con il punto di interruzione venga eseguito.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**). Per ulteriori informazioni sulle funzionalità di debug di base, vedere [Prima occhiata al debugger](../debugger/debugger-feature-tour.md).

    Puoi raggiungere il punto di interruzione in un file con estensione js o in un file *con estensione js* transpilato, a seconda del tipo di app, dei passaggi seguiti in precedenza e di altri fattori, ad esempio lo stato del browser. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

   * Se è necessario suddividere il codice in un file di origine TypeScript, JSX o *.vue* e non è possibile farlo, assicurarsi che l'ambiente sia configurato correttamente, come descritto nella sezione [Risoluzione dei problemi.](#troubleshooting_source_maps)

   * Se è necessario suddividere il codice nel codice in un file JavaScript transaccumulato (ad esempio, *app-bundle.js*) e non è possibile farlo, rimuovere il file di mappa di origine, *filename.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>Risoluzione dei problemi relativi ai punti di interruzione e alle mappe di origineTroubleshooting breakpoints and source

Se è necessario suddividere il codice in un file di origine TypeScript o JSX e non è possibile farlo, utilizzare **Connetti a processo** come descritto nei passaggi precedenti per connettere il debugger. Assicurarsi che l'ambiente sia configurato correttamente:

* Hai chiuso tutte le istanze del browser, incluse le estensioni di Chrome (utilizzando Task Manager), in modo da poter eseguire il browser in modalità di debug.
      
* Assicurarsi di [avviare il browser in modalità di debug](#prepare_the_browser_for_debugging).

* Assicurarsi che il file di mappa di origine includa il percorso relativo corretto del file di origine e che non includa prefissi non supportati, ad esempio *webpack:///*, che impedisce al debugger di Visual Studio di individuare un file di origine. Ad esempio, un riferimento come *webpack:///.app.tsx* potrebbe essere corretto in *./app.tsx*. È possibile eseguire questa operazione manualmente nel file di mappa di origine (che è utile per il test) o tramite una configurazione di compilazione personalizzata. Per ulteriori informazioni, vedere Generare mappe di [origine per il debug.](#generate_source_maps)

In alternativa, se è necessario suddividere il codice in un file di origine (ad esempio, `debugger;` *app.tsx*) e non è possibile farlo, provare a utilizzare l'istruzione nel file di origine o impostare punti di interruzione in Chrome Developer Tools (o F12 Tools for Microsoft Edge).

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Generare mapping di origine per il debug

Visual Studio è in grado di usare e generare mapping di origine su file di origine JavaScript. Questo è spesso necessario se l'origine è minimizzata o creata da un transpiler come Babel o TypeScript. Le opzioni disponibili dipendono dal tipo di progetto.

* Per impostazione predefinita, un progetto TypeScript in Visual Studio genera mapping di origine. Per ulteriori informazioni, consultate [Configurare le mappe di origine utilizzando un file tsconfig.json.](#configure_source_maps)

* In un progetto JavaScript, è possibile generare mappe di origine utilizzando un bundler come webpack e un compilatore come il compilatore TypeScript (o Babele), che è possibile aggiungere al progetto. Per il compilatore TypeScript, è inoltre necessario aggiungere un `sourceMap` file *tsconfig.json* e impostare l'opzione del compilatore. Per un esempio che illustra come eseguire questa operazione usando una configurazione webpack di base, vedere [Creare un'app Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Se non si ha familiarità con i mapping di origine, prima di continuare leggere [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Presentazione dei mapping di origine di JavaScript). 

Per configurare le impostazioni avanzate per i mapping di origine, usare un file *tsconfig.json* o le impostazioni progetto in un progetto TypeScript, ma non entrambi.

Per abilitare il debug con Visual Studio, è necessario assicurarsi che i riferimenti al file di origine nella mappa di origine generata siano corretti (questo potrebbe richiedere il test). Ad esempio, se si utilizza webpack, i riferimenti nel file di mappa di origine includono il prefisso *webpack:///,* che impedisce a Visual Studio di trovare un file di origine TypeScript o JSX. In particolare, quando si corregge questa situazione a scopo di debug, il riferimento al file di origine, ad esempio *app.tsx*, deve essere modificato da *un webpack:///./app.tsx* a un valore simile a *./app.tsx*, che consente il debug (il percorso è relativo al file di origine). The following example shows how you can configure source maps in webpack, which is one of the most common bundlers, so that they work with Visual Studio.

(Solo Webpack) Se state impostando il punto di interruzione in un file TypeScript di JSX (anziché in un file JavaScript transaccumulato), dovete aggiornare la configurazione del webpack. Ad esempio, in *webpack-config.js*, potrebbe essere necessario sostituire il codice seguente:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

con questo codice:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Si tratta di un'impostazione di solo sviluppo per abilitare il debug del codice lato client in Visual Studio.This is a development-only setting to enable debugging of client-side code in Visual Studio.

Per gli scenari complessi, gli strumenti del browser (**F12**) talvolta funzionano meglio per il debug, poiché non richiedono modifiche ai prefissi personalizzati.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>Configurare le mappe di origine usando un file tsconfig.jsonConfigure source maps using a tsconfig.json file

Se si aggiunge al progetto un file *tsconfig.json*, Visual Studio considera la directory radice come un progetto TypeScript. Per aggiungere il file, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, quindi scegliere Aggiungi > nuovo elemento > File di **configurazione JSON TypeScript**. Viene aggiunto al progetto un file *tsconfig.json* simile al seguente.

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>Opzioni del compilatore per tsconfig.json

* **inlineSourceMap**: Genera un singolo file con mappe di origine anziché creare una mappa di origine separata per ogni file di origine.
* **inlineSources**: Emetti l'origine insieme alle mappe di origine all'interno di un singolo file; richiede l'impostazione *di inlineSourceMap* o *sourceMap.*
* **mapRoot**: Specifica il percorso in cui il debugger deve trovare i file della mappa di origine (*.map*) anziché il percorso predefinito. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in una posizione diversa rispetto ai file con estensione *js*. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file con estensione *map*.
* **sourceMap**: Genera un file *.map* corrispondente.
* **sourceRoot**: Specifica il percorso in cui il debugger deve trovare i file TypeScript anziché i percorsi di origine. Usare questo flag se le origini di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

Per altri dettagli sulle opzioni del compilatore, vedere la pagina [Opzioni del compilatore](https://www.typescriptlang.org/docs/handbook/compiler-options.html) nel manuale di TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configurare le mappe di origine utilizzando le impostazioni di progetto (progetto TypeScript)

È anche possibile configurare le impostazioni di mapping di origine usando le proprietà del progetto, facendo clic con il pulsante destro del mouse sul progetto e quindi scegliendo **Progetto > Proprietà > Compilazione TypeScript > Debug**.

Sono disponibili le impostazioni del progetto seguenti.

* **Genera mappe di origine** (equivalente a **sourceMap** in *tsconfig.json):* genera il file *.map* corrispondente.
* **Specifica directory radice delle mappe di origine** (equivalente a **mapRoot** in *tsconfig.json*): specifica il percorso in cui il debugger deve trovare i file di mappa anziché i percorsi generati. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in un percorso diverso rispetto ai file con estensione js. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di mapping.
* **Specifica la directory radice dei file TypeScript** (equivalente a **sourceRoot** in *tsconfig.json*): specifica il percorso in cui il debugger deve trovare i file TypeScript anziché i percorsi di origine. Usare questo flag se i file di origine di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debug di JavaScript in file dinamici tramite Razor (ASP.NET)

::: moniker range=">=vs-2019"
A partire da Visual Studio 2019, Visual Studio fornisce il supporto per il debug solo per Chrome e Microsoft Edge (Chromium).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio supporta il debug solo per Internet Explorer e Chrome.
::: moniker-end

Tuttavia, non è possibile raggiungere automaticamente i punti di interruzione sui file generati con la sintassi Razor (cshtml, vbhtml). È possibile usare due approcci per il debug di questo tipo di file:

* **Inserire `debugger;` l'istruzione nel punto in cui si desidera interrompere**: In questo modo lo script dinamico interrompere l'esecuzione e avviare immediatamente il debug durante la creazione.
* **Caricare la pagina e aprire il documento dinamico in Visual Studio:** è necessario aprire il file dinamico durante il debug, impostare il punto di interruzione e aggiornare la pagina affinché questo metodo funzioni. Per trovare il file usare uno dei seguenti metodi, a seconda che si usi Chrome o Internet Explorer:

   Per Chrome, andare a **Esplora soluzioni > Documenti script > NomePagina**.

    > [!NOTE]
    > Se si usa Chrome è possibile che venga visualizzato un messaggio **No source is available between \<script> tags** (Nessuna origine disponibile tra i tag \<script>). Il messaggio non indica un problema ed è possibile procedere con il debug.

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (Chromium), utilizzare la stessa procedura di Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   In Internet Explorer, passare a **Esplora soluzioni > Documenti script > Windows Internet Explorer > NomePagina**.
   ::: moniker-end

Per altre informazioni, vedere [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Debug lato client di progetti ASP.NET in Google Chrome).
