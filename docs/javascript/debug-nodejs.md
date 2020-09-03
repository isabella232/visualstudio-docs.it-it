---
title: Eseguire il debug di un'app JavaScript o TypeScript
description: Visual Studio offre supporto per il debug di app JavaScript e TypeScript in Visual Studio
ms.date: 11/01/2019
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 801ea23430d13dbefd9498c57b07881235275961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285192"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Eseguire il debug di un'app JavaScript o TypeScript in Visual Studio

È possibile eseguire il debug di codice JavaScript e TypeScript con Visual Studio. È possibile impostare e raggiungere punti di interruzione, collegare il debugger, esaminare variabili, visualizzare lo stack di chiamate e usare altre funzionalità di debug.

> [!TIP]
> Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente. A seconda del tipo di sviluppo di app che si sta eseguendo, può essere necessario installare il **carico di lavoro Sviluppo Node.js** con Visual Studio.

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
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e Microsoft Edge (cromo). In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script lato client nelle app ASP.NET, vedere il post di Blog [debug di JavaScript in Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) e questo [post per Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome). Per il debug di TypeScript in ASP.NET Core, vedere anche [creare un'app ASP.NET Core con typescript](tutorial-aspnet-with-typescript.md).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e per Internet Explorer. In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script lato client nelle app ASP.NET, vedere il post di Blog relativo al [debug lato client dei progetti ASP.NET in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Per le applicazioni diverse da ASP.NET, seguire la procedura descritta qui.

### <a name="prepare-your-app-for-debugging"></a>Preparare l'app per il debug

Se l'origine è minimizzata o creata da un transpiler come TypeScript o Babel, è necessario usare [mapping di origine](#generate_source_maps) per ottenere la migliore esperienza di debug. Senza i mapping di origine, è comunque possibile collegare il debugger a uno script lato client in esecuzione. Tuttavia in molti casi è possibile impostare e raggiungere punti di interruzione solo nel file minimizzato o convertito tramite transpiler, e non nel file di origine. Ad esempio, in un'app Vue.js lo script minimizzato viene passato come stringa a un'istruzione `eval` e l'esecuzione efficace del codice istruzione per istruzione con il debugger di Visual Studio è possibile solo se si usano i mapping di origine. Negli scenari di debug complessi, è possibile usare anche gli strumenti Strumenti di sviluppo o F12 di Chrome per Microsoft Edge.

Per informazioni sulla generazione di mappe di origine, vedere [generare mappe di origine per il debug](#generate_source_maps).

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a> Preparare il browser per il debug

::: moniker range=">=vs-2019"
Per questo scenario, usare Microsoft Edge (cromo), attualmente denominato **Microsoft Edge beta** nell'IDE o Chrome.
::: moniker-end
::: moniker range="vs-2017"
Per questo scenario, usare Chrome.
::: moniker-end

1. Chiudere tutte le finestre per il browser di destinazione.

   Le altre istanze del browser possono impedire l'apertura del browser con il debug abilitato. (È possibile che le estensioni del browser siano in esecuzione e impediscano la modalità di debug completa, pertanto potrebbe essere necessario aprire Gestione attività per individuare le istanze impreviste di Chrome).

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (cromo), arrestare anche tutte le istanze di Chrome. Poiché entrambi i browser usano la codebase di cromo, questo fornisce i migliori risultati.
   ::: moniker-end

2. Avviare il browser con il debug abilitato.

    ::: moniker range=">=vs-2019"
    A partire da Visual Studio 2019, è possibile impostare il `--remote-debugging-port=9222` flag all'avvio del browser selezionando **Sfoglia con...** > dalla barra degli strumenti **debug** , quindi scegliendo **Aggiungi**e quindi impostando il flag nel campo **argomenti** . Usare un nome descrittivo diverso per il browser, ad esempio **Edge con debug** o **Chrome con debug**. Per informazioni dettagliate, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-v16.2).

    ![Imposta il browser per l'apertura con il debug abilitato](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    In alternativa, aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `msedge --remote-debugging-port=9222`

    o

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    Verrà avviato il browser con il debug abilitato.

    L'app non è ancora in esecuzione, quindi si ottiene una pagina del browser vuota.

### <a name="attach-the-debugger-to-client-side-script"></a>Connessione del debugger a uno script lato client

Per allungare il debugger da Visual Studio e raggiungere i punti di interruzione nel codice sul lato client, il debugger necessita di aiuto per identificare il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

1. Passare a Visual Studio e quindi impostare un punto di interruzione nel codice sorgente, che potrebbe essere un file JavaScript, un file TypeScript o un file JSX. Impostare il punto di interruzione in una riga di codice che consente i punti di interruzione, ad esempio un'istruzione return o una dichiarazione var.

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Per trovare il codice specifico in un file transpiled, usare **CTRL** + **F** (**modifica**  >  **trova e Sostituisci**  >  **ricerca veloce**).

    Per il codice lato client, per raggiungere un punto di interruzione in un file TypeScript, il file con *estensione VME*o JSX richiede in genere l'uso delle [mappe di origine](#generate_source_maps). Una mappa di origine deve essere configurata correttamente per supportare il debug in Visual Studio.

2. Selezionare il browser di destinazione come destinazione di debug in Visual Studio, quindi premere **CTRL** + **F5** (avvia**debug**  >  **senza debug**) per eseguire l'app nel browser.

    ::: moniker range=">=vs-2019"
    Se è stata creata una configurazione del browser con un nome descrittivo, sceglierla come destinazione di debug.
    ::: moniker-end

    L'app viene aperta in una nuova scheda del browser.

3. Scegliere **debug**  >  **Connetti a processo**.

    > [!TIP]
    > A partire da Visual Studio 2017, una volta eseguita la connessione al processo la prima volta seguendo questa procedura, è possibile riconnettersi rapidamente allo stesso processo scegliendo **debug**  >  **Riconnetti a processo**.

4. Nella finestra di dialogo **Connetti a processo** ottenere un elenco filtrato di istanze del browser a cui è possibile connettersi.
    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere il debugger corretto per il browser di destinazione, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge-Chromium)** nel campo **Connetti a** , digitare **Chrome** o **Edge** nella casella filtro per filtrare i risultati della ricerca.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **codice Webkit** nel campo **Connetti a** , digitare **Chrome** nella casella filtro per filtrare i risultati della ricerca.
    ::: moniker-end

5. Selezionare il processo browser con la porta host corretta (localhost in questo esempio) e selezionare **Connetti**.

    La porta (ad esempio, 1337) può essere visualizzata anche nel campo **titolo** per facilitare la selezione dell'istanza del browser corretta.

    ::: moniker range=">=vs-2019"
    Nell'esempio seguente viene illustrato il modo in cui viene ricercato il browser Microsoft Edge (cromo).

    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili ai Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.
    ::: moniker-end

    > [!TIP]
    > Se il debugger non viene collegato e viene visualizzato il messaggio "Impossibile avviare l'adattatore di debug" o "Impossibile connettersi al processo. Operazione non valida nello stato corrente. "utilizzare Gestione attività di Windows per chiudere tutte le istanze del browser di destinazione prima di avviare il browser in modalità di debug. Le estensioni del browser possono essere in esecuzione e impedire la modalità di debug completa.

6. Poiché è possibile che il codice con il punto di interruzione sia già stato eseguito, aggiornare la pagina del browser. Se necessario, eseguire un'azione per provocare l'esecuzione del codice con il punto di interruzione.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**). Per ulteriori informazioni sulle funzionalità di debug di base, vedere [la prima occhiata al debugger](../debugger/debugger-feature-tour.md).

    È possibile raggiungere il punto di interruzione in un file di origine o in un file con estensione *JS* transpiled, a seconda del tipo di app, in cui sono stati eseguiti i passaggi precedenti e altri fattori, ad esempio lo stato del browser. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

   * Se è necessario suddividere il codice in un file di origine TypeScript, JSX o *VME* e non è possibile eseguire questa operazione, assicurarsi che l'ambiente sia configurato correttamente, come descritto nella sezione [risoluzione dei problemi](#troubleshooting_source_maps) .

   * Se è necessario suddividere il codice in un file JavaScript transpiled (ad esempio *app-bundle.js*) e non è possibile eseguire questa operazione, rimuovere il file di mapping di origine *filename.js. map*.

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a> Risoluzione dei problemi relativi a punti di interruzione e mappe di origine

Se è necessario suddividere il codice in un file di origine TypeScript o JSX e non è possibile eseguire questa operazione, usare **Connetti a processo** come descritto nei passaggi precedenti per la connessione del debugger. Assicurarsi che l'ambiente sia configurato correttamente:

* Tutte le istanze del browser sono state chiuse, incluse le estensioni Chrome (mediante Gestione attività), in modo che sia possibile eseguire il browser in modalità di debug.
      
* Assicurarsi [di avviare il browser in modalità di debug](#prepare_the_browser_for_debugging).

* Verificare che il file di mapping di origine includa il percorso relativo corretto per il file di origine e che non includa prefissi non supportati, ad esempio *Webpack:///*, che impedisce al debugger di Visual Studio di individuare un file di origine. Ad esempio, un riferimento come *Webpack:///.app.TSX* potrebbe essere corretto in *./app.TSX*. Questa operazione può essere eseguita manualmente nel file di mappa di origine (utile per il test) o tramite una configurazione di compilazione personalizzata. Per altre informazioni, vedere [generare mappe di origine per il debug](#generate_source_maps).

In alternativa, se è necessario suddividere il codice in un file di origine (ad esempio, *app. TSX*) e non è possibile eseguire questa operazione, provare `debugger;` a usare l'istruzione nel file di origine o impostare i punti di interruzione nel strumenti di sviluppo di Chrome (o negli strumenti F12 per Microsoft Edge).

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> Generare mapping di origine per il debug

Visual Studio è in grado di usare e generare mapping di origine su file di origine JavaScript. Questo è spesso necessario se l'origine è minimizzata o creata da un transpiler come Babel o TypeScript. Le opzioni disponibili dipendono dal tipo di progetto.

* Per impostazione predefinita, un progetto TypeScript in Visual Studio genera mapping di origine. Per altre informazioni, vedere [configurare i mapping di origine usando un tsconfig.jssu file](#configure_source_maps).

* In un progetto JavaScript, è possibile generare mappe di origine usando un bundler come Webpack e un compilatore come il compilatore TypeScript (o Babel), che è possibile aggiungere al progetto. Per il compilatore TypeScript, è necessario aggiungere anche un *tsconfig.jssu* file e impostare l' `sourceMap` opzione del compilatore. Per un esempio che illustra come eseguire questa operazione usando una configurazione webpack di base, vedere [Creare un'app Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Se non si ha familiarità con i mapping di origine, prima di continuare leggere [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Presentazione dei mapping di origine di JavaScript). 

Per configurare le impostazioni avanzate per i mapping di origine, usare un file *tsconfig.json* o le impostazioni progetto in un progetto TypeScript, ma non entrambi.

Per abilitare il debug con Visual Studio, è necessario assicurarsi che i riferimenti al file di origine nella mappa di origine generata siano corretti. questa operazione potrebbe richiedere dei test. Se ad esempio si usa Webpack, i riferimenti nel file di mappa di origine includono il prefisso *Webpack:///* , che impedisce a Visual Studio di trovare un file di origine TYPESCRIPT o JSX. In particolare, quando si corregge questa operazione a scopo di debug, il riferimento al file di origine (ad esempio, *app. TSX*) deve essere modificato da un elemento come *Webpack:///./app.TSX* a un elemento simile a *./app.TSX*, che consente il debug (il percorso è relativo al file di origine). Nell'esempio seguente viene illustrato come è possibile configurare le mappe di origine in Webpack, uno dei bundleri più comuni, in modo che funzionino con Visual Studio.

(Solo Webpack) Se si imposta il punto di interruzione in un TypeScript di file JSX (anziché in un file JavaScript transpiled), è necessario aggiornare la configurazione di Webpack. Ad esempio, in *webpack-config.js*, potrebbe essere necessario sostituire il codice seguente:

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

Si tratta di un'impostazione di solo sviluppo per abilitare il debug del codice sul lato client in Visual Studio.

Per gli scenari complessi, gli strumenti del browser (**F12**) a volte funzionano meglio per il debug, in quanto non richiedono modifiche ai prefissi personalizzati.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a> Configurare i mapping di origine usando un tsconfig.jssu file

Se si aggiunge al progetto un file *tsconfig.json*, Visual Studio considera la directory radice come un progetto TypeScript. Per aggiungere il file, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni, quindi scegliere **aggiungi > nuovo elemento > file di configurazione JSON di typescript**. Viene aggiunto al progetto un file *tsconfig.json* simile al seguente.

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

* **inlineSourceMap**: creare un singolo file con mapping di origine anziché creare una mappa di origine separata per ogni file di origine.
* **inlineSources**: creare l'origine insieme alle mappe di origine all'interno di un singolo file. richiede l'impostazione di *inlineSourceMap* o *sourceMap* .
* **MAPROOT**: specifica il percorso in cui il debugger deve trovare i file della mappa di origine (con*estensione map*) anziché il percorso predefinito. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in una posizione diversa rispetto ai file con estensione *js*. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file con estensione *map*.
* **sourceMap**: genera un file con *estensione map* corrispondente.
* **sourceRoot**: specifica il percorso in cui il debugger deve trovare i file typescript anziché i percorsi di origine. Usare questo flag se le origini di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

Per altri dettagli sulle opzioni del compilatore, vedere la pagina [Opzioni del compilatore](https://www.typescriptlang.org/docs/handbook/compiler-options.html) nel manuale di TypeScript.

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>Configurare i mapping di origine usando le impostazioni di progetto (progetto TypeScript)

È anche possibile configurare le impostazioni di mapping di origine usando le proprietà del progetto, facendo clic con il pulsante destro del mouse sul progetto e quindi scegliendo **Progetto > Proprietà > Compilazione TypeScript > Debug**.

Sono disponibili le impostazioni del progetto seguenti.

* **Genera mapping di origine** (equivalente **a sourceMap** in *tsconfig.json*): genera il file *. map* corrispondente.
* **Specificare la directory radice dei mapping di origine** (equivalente a **MAPROOT** in *tsconfig.json*): specifica il percorso in cui il debugger deve trovare i file della mappa invece dei percorsi generati. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in un percorso diverso rispetto ai file con estensione js. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di mapping.
* **Specificare la directory radice dei file typescript** (equivalente a **sourceRoot** in *tsconfig.json*): specifica il percorso in cui il debugger deve trovare i file typescript invece dei percorsi di origine. Usare questo flag se i file di origine di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debug di JavaScript in file dinamici tramite Razor (ASP.NET)

::: moniker range=">=vs-2019"
A partire da Visual Studio 2019, Visual Studio fornisce il supporto per il debug solo per Chrome e Microsoft Edge (cromo).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio supporta il debug solo per Internet Explorer e Chrome.
::: moniker-end

Tuttavia, non è possibile raggiungere automaticamente i punti di interruzione nei file generati con sintassi Razor (cshtml, vbhtml). È possibile usare due approcci per il debug di questo tipo di file:

* **Inserire l' `debugger;` istruzione in cui si desidera interrompere**l'esecuzione, in modo che lo script dinamico interrompa l'esecuzione e avvii immediatamente il debug durante la creazione.
* **Caricare la pagina e aprire il documento dinamico in Visual Studio**: è necessario aprire il file dinamico durante il debug, impostare il punto di interruzione e aggiornare la pagina per il funzionamento di questo metodo. Per trovare il file usare uno dei seguenti metodi, a seconda che si usi Chrome o Internet Explorer:

   Per Chrome, andare a **Esplora soluzioni > Documenti script > NomePagina**.

    > [!NOTE]
    > Quando si usa Chrome, è possibile che venga ricevuto un messaggio **non è disponibile alcuna origine tra i \<script> tag**. Il messaggio non indica un problema ed è possibile procedere con il debug.

   ::: moniker range=">=vs-2019"
   Per Microsoft Edge (cromo), usare la stessa procedura di Chrome.
   ::: moniker-end

   ::: moniker range="vs-2017"
   In Internet Explorer, passare a **Esplora soluzioni > Documenti script > Windows Internet Explorer > NomePagina**.
   ::: moniker-end

Per altre informazioni, vedere [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Debug lato client di progetti ASP.NET in Google Chrome).
