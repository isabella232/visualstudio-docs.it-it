---
title: Eseguire il debug di un'app JavaScript o TypeScript
description: Visual Studio offre supporto per il debug di app JavaScript e TypeScript in Visual Studio
ms.date: 11/01/2019
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 6287ccebaca054bc639f7317d1a6e3e2d9f6f8457c025682a25cddb0a043c2b7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370944"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Eseguire il debug di un'app JavaScript o TypeScript in Visual Studio

È possibile eseguire il debug di codice JavaScript e TypeScript con Visual Studio. È possibile impostare e raggiungere punti di interruzione, collegare il debugger, esaminare variabili, visualizzare lo stack di chiamate e usare altre funzionalità di debug.

> [!TIP]
> Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente. A seconda del tipo di sviluppo di app che si sta eseguendo, può essere necessario installare il **carico di lavoro Sviluppo Node.js** con Visual Studio.

## <a name="debug-server-side-script"></a>Eseguire il debug di script lato server

1. Con il progetto aperto in Visual Studio, aprire un file JavaScript lato server (ad esempio *server.js*) e fare clic nella barra di navigazione sinistra per impostare un punto di interruzione:

    ![Screenshot della finestra Visual Studio codice javascript. Un punto rosso nella barra di spostamento a sinistra indica che è impostato un punto di interruzione.](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Per eseguire l'app premere **F5** (**Debug** > **Avvia debug**).

    Il debugger sospende l'esecuzione nel punto di interruzione impostato (l'istruzione corrente è contrassegnata in giallo). A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Premere **F5** per continuare con l'esecuzione dell'app.

1. Per usare Chrome Developer Tools o gli Strumenti F12, premere **F12**. È possibile usare questi strumenti per esaminare il modello DOM e interagire con l'app mediante la console JavaScript.

## <a name="debug-client-side-script"></a>Debug di script lato client

::: moniker range=">=vs-2019"
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e Microsoft Edge (Chromium). In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script lato client nelle app ASP.NET, vedere il post di blog Debug JavaScript in Microsoft Edge (Eseguire il debug di [JavaScript in Microsoft Edge)](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) e questo [post per Google Chrome.](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome) Per il debug di TypeScript in ASP.NET Core, vedere anche [Creare un'app ASP.NET Core con TypeScript.](tutorial-aspnet-with-typescript.md)
::: moniker-end
::: moniker range="vs-2017"
Visual Studio offre il supporto per il debug lato client solo per Chrome Internet Explorer. In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script lato client nelle ASP.NET, vedere il post di blog Debug lato client di ASP.NET [in Google Chrome.](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)
::: moniker-end

Per le applicazioni diverse ASP.NET, seguire la procedura descritta qui.

### <a name="prepare-your-app-for-debugging"></a>Preparare l'app per il debug

Se l'origine è minimizzata o creata da un transpiler come TypeScript o Babel, è necessario usare [mapping di origine](#generate_source_maps) per ottenere la migliore esperienza di debug. Senza i mapping di origine, è comunque possibile collegare il debugger a uno script lato client in esecuzione. Tuttavia in molti casi è possibile impostare e raggiungere punti di interruzione solo nel file minimizzato o convertito tramite transpiler, e non nel file di origine. Ad esempio, in un'app Vue.js lo script minimizzato viene passato come stringa a un'istruzione `eval` e l'esecuzione efficace del codice istruzione per istruzione con il debugger di Visual Studio è possibile solo se si usano i mapping di origine. In scenari di debug complessi, è anche possibile usare Chrome Strumenti di sviluppo o F12 Tools per Microsoft Edge.

Per informazioni su come generare le mappe di origine, vedere [Generare mappe di origine per il debug.](#generate_source_maps)

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a> Preparare il browser per il debug

::: moniker range=">=vs-2019"
Per questo scenario, usare Microsoft Edge (Chromium), attualmente denominato **Microsoft Edge Beta** nell'IDE, o Chrome.
::: moniker-end
::: moniker range="vs-2017"
Per questo scenario, usare Chrome.
::: moniker-end

1. Chiudere tutte le finestre per il browser di destinazione.

   Altre istanze del browser possono impedire l'apertura del browser con il debug abilitato. Le estensioni del browser potrebbero essere in esecuzione e impedire la modalità di debug completo, quindi potrebbe essere necessario aprire Gestione attività per trovare istanze impreviste di Chrome.

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (Chromium), arrestare anche tutte le istanze di Chrome. Poiché entrambi i browser usano la codebase chromium, questo offre i risultati migliori.
   ::: moniker-end

2. Avviare il browser con il debug abilitato.

    ::: moniker range=">=vs-2019"
    A partire da Visual Studio 2019, è possibile impostare il flag all'avvio del browser selezionando Esplora con > dalla barra degli strumenti `--remote-debugging-port=9222` **Debug,**  quindi scegliendo Aggiungi e quindi impostando il flag nel campo Argomenti.  Usare un nome descrittivo diverso per il browser, ad esempio **Edge with Debugging (Edge con debug)** **o Chrome with Debugging (Chrome con debug).** Per informazioni dettagliate, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-v16.2).

    ![Impostare il browser per l'apertura con il debug abilitato](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    In alternativa, aprire il **comando Esegui** dal Windows **Start** (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

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

Per collegare il debugger da Visual Studio e individuare i punti di interruzione nel codice lato client, il debugger deve aiutare a identificare il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

1. Passare a Visual Studio e quindi impostare un punto di interruzione nel codice sorgente, che potrebbe essere un file JavaScript, un file TypeScript o un file JSX. Impostare il punto di interruzione in una riga di codice che consente punti di interruzione, ad esempio un'istruzione return o una dichiarazione var.

    ![Screenshot della finestra Visual Studio codice. Viene selezionata un'istruzione return e un punto rosso nella barra di spostamento a sinistra indica che è impostato un punto di interruzione.](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Per trovare il codice specifico in un file transpiled, usare **CTRL** + **F** (**Modifica** Ricerca  >  **e sostituisci** Ricerca  >  **rapida**).

    Per il codice lato client, per accedere a un punto di interruzione in un file TypeScript, con estensione *vue* o JSX è in genere necessario usare le [mappe di origine](#generate_source_maps). Un source map deve essere configurato correttamente per supportare il debug in Visual Studio.

2. Selezionare il browser di destinazione come destinazione di debug in Visual Studio, quindi premere **CTRL** + **F5** (**Debug** Avvia senza eseguire debug ) per eseguire l'app  >  nel browser.

    ::: moniker range=">=vs-2019"
    Se è stata creata una configurazione del browser con un nome descrittivo, sceglierne una come destinazione di debug.
    ::: moniker-end

    L'app viene aperta in una nuova scheda del browser.

3. Scegliere **Debug**  >  **Attach to Process (Esegui debug connessione a processo).**

    > [!TIP]
    > A partire da Visual Studio 2017, dopo la prima connessione al processo seguendo questi passaggi, è possibile ricollegare rapidamente allo stesso processo scegliendo **Debug** Ricollegare a  >  **Elabora**.

4. Nella finestra **di dialogo Associa a** processo ottenere un elenco filtrato di istanze del browser a cui è possibile connettersi.
    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere il debugger corretto per il browser di destinazione, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge - Chromium)** nel campo Collega a, digitare **chrome** o **edge** nella casella del filtro per filtrare i risultati della ricerca. 
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **Webkit code** (Codice Webkit) nel campo **Attach to** (Collega a) e digitare **chrome** nella casella del filtro per filtrare i risultati della ricerca.
    ::: moniker-end

5. Selezionare il processo del browser con la porta host corretta (localhost in questo esempio) e selezionare **Collega**.

    La porta (ad esempio, 1337) può essere visualizzata anche nel campo **Titolo** per consentire la selezione dell'istanza corretta del browser.

    ::: moniker range=">=vs-2019"
    Nell'esempio seguente viene illustrato l'aspetto del browser Microsoft Edge (Chromium).

    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili ai Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se il debugger non si collega e viene visualizzato il messaggio "Impossibile avviare l'adattatore di debug" o "Impossibile connettersi al processo. Un'operazione non è valida nello stato corrente.", usare il Windows Gestione attività per chiudere tutte le istanze del browser di destinazione prima di avviare il browser in modalità di debug. Le estensioni del browser potrebbero essere in esecuzione e impedire la modalità di debug completo.

6. Poiché il codice con il punto di interruzione potrebbe essere già stato eseguito, aggiornare la pagina del browser. Se necessario, eseguire un'azione per fare in modo che il codice con il punto di interruzione sia eseguito.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**). Per altre informazioni sulle funzionalità di debug di base, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

    È possibile che venga raggiunto il punto di interruzione in un file.jso in un file di origine transpiled, *a* seconda del tipo di app, dei passaggi seguiti in precedenza e di altri fattori, ad esempio lo stato del browser. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

   * Se è necessario suddividere il codice in un file di origine TypeScript, JSX o *vue* e non è possibile [](#troubleshooting_source_maps) eseguire questa operazione, assicurarsi che l'ambiente sia configurato correttamente, come descritto nella sezione Risoluzione dei problemi.

   * Se è necessario suddividere il codice in un file JavaScript transpiled (ad *esempio,app-bundle.js*) e non è possibile eseguire questa operazione, rimuovere il file source map, *filename.js.map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a> Risoluzione dei problemi relativi ai punti di interruzione e alle mappe di origine

Se è necessario suddividere il codice in un file di origine TypeScript o JSX e non è possibile eseguire questa operazione, usare **Associa** a processo come descritto nei passaggi precedenti per collegare il debugger. Assicurarsi che l'ambiente sia configurato correttamente:

* Sono state chiuse tutte le istanze del browser, incluse le estensioni di Chrome (usando il Gestione attività), in modo da poter eseguire il browser in modalità di debug.
      
* Assicurarsi di avviare [il browser in modalità di debug](#prepare_the_browser_for_debugging).

* Assicurarsi che il file source map includa il percorso relativo corretto del file di origine e che non includa prefissi non supportati, ad esempio *webpack:///*, che impedisce al debugger di Visual Studio di individuare un file di origine. Ad esempio, un riferimento *come webpack:///.app.tsx* potrebbe essere corretto in *./app.tsx*. È possibile eseguire questa operazione manualmente nel file source map (utile per il test) o tramite una configurazione di compilazione personalizzata. Per altre informazioni, vedere Generare [mappe di origine per il debug.](#generate_source_maps)

In alternativa, se è necessario suddividere il codice in un file di origine (ad *esempio, app.tsx*) e non è possibile eseguire questa operazione, provare a usare l'istruzione nel file di origine o impostare punti di interruzione in `debugger;` Chrome Strumenti di sviluppo (o F12 Tools per Microsoft Edge).

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Generare mapping di origine per il debug

Visual Studio è in grado di usare e generare mapping di origine su file di origine JavaScript. Questo è spesso necessario se l'origine è minimizzata o creata da un transpiler come Babel o TypeScript. Le opzioni disponibili dipendono dal tipo di progetto.

* Per impostazione predefinita, un progetto TypeScript in Visual Studio genera mapping di origine. Per altre informazioni, vedere [Configurare le mappe di origine usando un tsconfig.jsnel file](#configure_source_maps).

* In un progetto JavaScript è possibile generare mappe di origine usando un bundler come webpack e un compilatore come il compilatore TypeScript (o Babel), che è possibile aggiungere al progetto. Per il compilatore TypeScript, è anche necessario aggiungere untsconfig.js *nel* file e impostare l'opzione `sourceMap` del compilatore . Per un esempio che illustra come eseguire questa operazione usando una configurazione webpack di base, vedere [Creare un'app Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Se non si ha familiarità con i mapping di origine, prima di continuare leggere [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Presentazione dei mapping di origine di JavaScript). 

Per configurare le impostazioni avanzate per i mapping di origine, usare un file *tsconfig.json* o le impostazioni progetto in un progetto TypeScript, ma non entrambi.

Per abilitare il debug Visual Studio, è necessario assicurarsi che i riferimenti al file di origine nel file di source map origine generato siano corretti (potrebbe essere necessario eseguire test). Ad esempio, se si usa webpack, i riferimenti nel file source map includono il prefisso *webpack:///,* che impedisce Visual Studio di trovare un file di origine TypeScript o JSX. In particolare, quando si corregge questo problema a scopo di debug, il riferimento al file di origine (ad esempio *app.tsx)* deve essere modificato da un elemento come *webpack:///./app.tsx a* un elemento come *./app.tsx,* che abilita il debug (il percorso è relativo al file di origine). L'esempio seguente illustra come configurare le mappe di origine in webpack, uno dei bundler più comuni, in modo che funzionino con Visual Studio.

(solo Webpack) Se si imposta il punto di interruzione in un file TypeScript di JSX (anziché in un file JavaScript transpiled), è necessario aggiornare la configurazione di webpack. Ad esempio, in *webpack-config.js*, potrebbe essere necessario sostituire il codice seguente:

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

Con questo:

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

Si tratta di un'impostazione di solo sviluppo per abilitare il debug del codice lato client in Visual Studio.

Per scenari complessi, gli strumenti del browser (**F12**) a volte funzionano meglio per il debug, perché non richiedono modifiche ai prefissi personalizzati.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a> Configurare le mappe di origine usando un tsconfig.jsnel file

Se si aggiunge al progetto un file *tsconfig.json*, Visual Studio considera la directory radice come un progetto TypeScript. Per aggiungere il file, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e quindi scegliere Aggiungi > nuovo elemento > file di configurazione **JSON TypeScript**. Viene aggiunto al progetto un file *tsconfig.json* simile al seguente.

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

* **inlineSourceMap:** genera un singolo file con mappe di origine invece di creare un source map separato per ogni file di origine.
* **inlineSources:** genera l'origine insieme alle mappe di origine all'interno di un singolo file; richiede *l'impostazione di inlineSourceMap* o *sourceMap.*
* **mapRoot:** specifica il percorso in cui il debugger deve trovare source map file (*.map*) anziché il percorso predefinito. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in una posizione diversa rispetto ai file con estensione *js*. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file con estensione *map*.
* **sourceMap:** genera un file *con estensione map* corrispondente.
* **sourceRoot:** specifica il percorso in cui il debugger deve trovare i file TypeScript anziché i percorsi di origine. Usare questo flag se le origini di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

Per altri dettagli sulle opzioni del compilatore, vedere la pagina [Opzioni del compilatore](https://www.typescriptlang.org/docs/handbook/compiler-options.html) nel manuale di TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configurare le mappe di origine usando le impostazioni del progetto (progetto TypeScript)

È anche possibile configurare le impostazioni di mapping di origine usando le proprietà del progetto, facendo clic con il pulsante destro del mouse sul progetto e quindi scegliendo **Progetto > Proprietà > Compilazione TypeScript > Debug**.

Sono disponibili le impostazioni del progetto seguenti.

* **Genera mappe di origine** (equivalenti **a sourceMap** in *tsconfig.jsin*): genera il file con *estensione map* corrispondente.
* **Specificare la directory radice delle** mappe di origine (equivalente a **mapRoot** in *tsconfig.jsin*): specifica il percorso in cui il debugger deve trovare i file di mapping anziché i percorsi generati. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in un percorso diverso rispetto ai file con estensione js. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di mapping.
* **Specificare la directory radice** dei file TypeScript (equivalente a **sourceRoot** intsconfig.js *in*): specifica il percorso in cui il debugger deve trovare i file TypeScript anziché i percorsi di origine. Usare questo flag se i file di origine di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debug di JavaScript in file dinamici tramite Razor (ASP.NET)

::: moniker range=">=vs-2019"
A partire Visual Studio 2019, Visual Studio il supporto per il debug solo per Chrome e Microsoft Edge (Chromium).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio supporta il debug solo per Internet Explorer e Chrome.
::: moniker-end

Tuttavia, non è possibile raggiunto automaticamente i punti di interruzione nei file generati con sintassi Razor (cshtml, vbhtml). È possibile usare due approcci per il debug di questo tipo di file:

* **Inserire `debugger;` l'istruzione in cui si vuole interrompere**: in questo modo lo script dinamico arresta l'esecuzione e avvia immediatamente il debug durante la creazione.
* Caricare la pagina e aprire il documento dinamico **in Visual Studio:** è necessario aprire il file dinamico durante il debug, impostare il punto di interruzione e aggiornare la pagina per il funzionamento di questo metodo. Per trovare il file usare uno dei seguenti metodi, a seconda che si usi Chrome o Internet Explorer:

   Per Chrome, andare a **Esplora soluzioni > Documenti script > NomePagina**.

    > [!NOTE]
    > Quando si usa Chrome, è possibile che venga visualizzato un messaggio che **indica che non è disponibile alcuna origine tra i \<script> tag**. Il messaggio non indica un problema ed è possibile procedere con il debug.

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (Chromium), usare la stessa procedura di Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   In Internet Explorer, passare a **Esplora soluzioni > Documenti script > Windows Internet Explorer > NomePagina**.
   ::: moniker-end

Per altre informazioni, vedere [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Debug lato client di progetti ASP.NET in Google Chrome).
