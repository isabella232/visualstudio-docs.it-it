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
ms.openlocfilehash: 5fbaa25146c9e06f3a12b90ab2d6ae124fbbd189
ms.sourcegitcommit: ee9c55616a22addc89cf1cf1942bf371d73e2e11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2019
ms.locfileid: "73618099"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>Eseguire il debug di un'app JavaScript o TypeScript in Visual Studio

È possibile eseguire il debug di codice JavaScript e TypeScript con Visual Studio. È possibile impostare e raggiungere punti di interruzione, collegare il debugger, esaminare variabili, visualizzare lo stack di chiamate e usare altre funzionalità di debug.

> [!TIP]
> Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente. A seconda del tipo di sviluppo di app che si sta eseguendo, può essere necessario installare il **carico di lavoro Sviluppo Node.js** con Visual Studio.

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
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e Microsoft Edge (cromo). In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script lato client nelle app ASP.NET, vedere il post di Blog [debug di JavaScript in Microsoft Edge](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/) e questo [post per Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome).
::: moniker-end
::: moniker range="vs-2017"
Visual Studio fornisce il supporto per il debug lato client solo per Chrome e per Internet Explorer. In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML. Per il debug di script lato client nelle app ASP.NET, vedere il post di Blog relativo al [debug lato client dei progetti ASP.NET in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/).
::: moniker-end

Se l'origine è minimizzata o creata da un transpiler come TypeScript o Babel, è necessario usare [mapping di origine](#generate_sourcemaps) per ottenere la migliore esperienza di debug. Senza i mapping di origine, è comunque possibile collegare il debugger a uno script lato client in esecuzione. Tuttavia in molti casi è possibile impostare e raggiungere punti di interruzione solo nel file minimizzato o convertito tramite transpiler, e non nel file di origine. Ad esempio, in un'app Vue.js lo script minimizzato viene passato come stringa a un'istruzione `eval` e l'esecuzione efficace del codice istruzione per istruzione con il debugger di Visual Studio è possibile solo se si usano i mapping di origine. Negli scenari di debug complessi è invece possibile usare gli strumenti Strumenti di sviluppo o F12 di Chrome per Microsoft Edge.

### <a name="attach-the-debugger-to-client-side-script"></a>Connessione del debugger a uno script lato client

Per allungare il debugger da Visual Studio e raggiungere i punti di interruzione nel codice sul lato client, il debugger necessita di aiuto per identificare il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità.

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

2. Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker range=">=vs-2019"
    oppure `msedge --remote-debugging-port=9222`
    ::: moniker-end

    Verrà avviato il browser con il debug abilitato.

    ::: moniker range=">=vs-2019"

    > [!TIP]
    > A partire da Visual Studio 2019, è possibile impostare il flag di `--remote-debugging-port` all'avvio del browser selezionando **Sfoglia con...** > dalla barra degli strumenti **debug** , quindi scegliendo **Aggiungi**e quindi impostando il flag nel campo **argomenti** . Usare un nome descrittivo diverso per il browser, ad esempio **Edge con debug** o **Chrome con debug**. Per informazioni dettagliate, vedere le [note sulla versione](/visualstudio/releases/2019/release-notes-v16.2).

    ![Imposta il browser per l'apertura con il debug abilitato](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    ::: moniker-end

    L'app non è ancora in esecuzione, quindi si ottiene una pagina del browser vuota.

3. Passare a Visual Studio e quindi impostare un punto di interruzione nel codice sorgente, che potrebbe essere un file JavaScript, un file TypeScript o un file JSX. Impostare il punto di interruzione in una riga di codice che consente i punti di interruzione, ad esempio un'istruzione return o una dichiarazione var.

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Per trovare il codice specifico in un file transpiled, usare **Ctrl**+**F** (**modifica** > **trova e Sostituisci** > **ricerca veloce**).

    Per il codice lato client, per raggiungere un punto di interruzione in un file TypeScript o JSX è in genere necessario usare [mapping modo](#generate_sourcemaps). Una sourcemap deve essere configurata correttamente per supportare il debug in Visual Studio.

4. (Solo Webpack) Seguire le istruzioni descritte in [generare mapping modo](#generate_sourcemaps).

5. Selezionare il browser di destinazione come destinazione di debug in Visual Studio, quindi premere **Ctrl**+**F5** (**debug** > **Avvia senza eseguire debug**) per eseguire l'app nel browser.

    L'app viene aperta in una nuova scheda del browser.

6. Scegliere **Debug** > **Associa a processo**.

7. Nella finestra di dialogo **Connetti a processo** ottenere un elenco filtrato di istanze del browser a cui è possibile connettersi.

    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere il browser di destinazione corretto, **JavaScript (Chrome)** o **JavaScript (Microsoft Edge-Chromium)** nel campo **Connetti a** , digitare **Chrome** o **Edge** nella casella filtro per filtrare i risultati della ricerca. Se è stata creata una configurazione del browser con un nome descrittivo, scegliere invece.
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **codice Webkit** nel campo **Connetti a** , digitare **Chrome** nella casella filtro per filtrare i risultati della ricerca.
    ::: moniker-end

8. Selezionare il processo browser con la porta host corretta (localhost in questo esempio) e selezionare **Connetti**.

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

9. Poiché è possibile che il codice con il punto di interruzione sia già stato eseguito, aggiornare la pagina del browser. Se necessario, eseguire un'azione per provocare l'esecuzione del codice con il punto di interruzione.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**).

    È possibile raggiungere il punto di interruzione sia nel file con *estensione js* transpiled che nel file di origine, a seconda dei passaggi seguiti in precedenza, insieme all'ambiente e allo stato del browser. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

   * Se è necessario suddividere il codice in un file di origine TypeScript o JSX e non è possibile eseguire questa operazione, usare **Connetti a processo** come descritto nei passaggi precedenti per la connessione del debugger. Assicurarsi che l'ambiente sia configurato correttamente:

      * Tutte le istanze del browser sono state chiuse, incluse le estensioni Chrome (mediante Gestione attività), in modo che sia possibile eseguire il browser in modalità di debug. Assicurarsi di avviare il browser in modalità di debug.

      * Verificare che il file sourcemap includa un riferimento al file di origine che non includa prefissi non supportati, ad esempio *Webpack:///* , che impedisce al debugger di Visual Studio di individuare *app. TSX*. Ad esempio, questo riferimento potrebbe essere corretto in *./app.TSX*. Questa operazione può essere eseguita manualmente nel file sourcemap o tramite una modifica personalizzata della compilazione.

       In alternativa, se è necessario suddividere il codice in un file di origine (ad esempio, * app. TSX) e non è possibile eseguire questa operazione, provare a usare l'istruzione `debugger;` nel file di origine o impostare i punti di interruzione nel Strumenti di sviluppo di Chrome (o negli strumenti F12 per Microsoft Edge).

   * Se è necessario suddividere il codice in un file JavaScript transpiled (ad esempio, *app-bundle. js*) e non è possibile eseguire questa operazione, rimuovere il file sourcemap, *filename. js. map*.

     > [!TIP]
     > Dopo aver eseguito per la prima volta l'associazione al processo seguendo questa procedura, è possibile ripetere rapidamente l'associazione allo stesso processo in Visual Studio 2017 scegliendo **Debug** > **Riassocia a processo**.

## <a name="generate_sourcemaps"></a> Generare mapping di origine per il debug

Visual Studio è in grado di usare e generare mapping di origine su file di origine JavaScript. Questo è spesso necessario se l'origine è minimizzata o creata da un transpiler come Babel o TypeScript. Le opzioni disponibili dipendono dal tipo di progetto.

* Per impostazione predefinita, un progetto TypeScript in Visual Studio genera mapping di origine.

* In un progetto JavaScript è necessario generare mapping di origine usando un bundler come webpack e un compilatore, ad esempio il compilatore TypeScript (o Babel), che può essere aggiunto al progetto. Per il compilatore TypeScript è necessario aggiungere anche un file *tsconfig.json*. Per un esempio che illustra come eseguire questa operazione usando una configurazione webpack di base, vedere [Creare un'app Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Se non si ha familiarità con i mapping di origine, prima di continuare leggere [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Presentazione dei mapping di origine di JavaScript). 

Per configurare le impostazioni avanzate per i mapping di origine, usare un file *tsconfig.json* o le impostazioni progetto in un progetto TypeScript, ma non entrambi.

Per abilitare il debug con Visual Studio, è necessario assicurarsi che i riferimenti al file di origine nel sourcemap generato siano corretti. Se ad esempio si usa Webpack, i riferimenti nel file sourcemap includono il prefisso *Webpack:///* , che impedisce a Visual Studio di trovare un file di origine TYPESCRIPT o JSX. In particolare, quando si corregge questa operazione a scopo di debug, il riferimento al file di origine (ad esempio, *app. TSX*) deve essere modificato da un elemento come *Webpack:///./app.TSX* a un elemento simile a *./app.TSX*, che consente il debug (il il percorso è relativo al file di origine. Nell'esempio seguente viene illustrato come è possibile correggere mapping modo con Webpack, uno dei bundle più comuni.

(Solo Webpack) Se si imposta il punto di interruzione in un TypeScript di file JSX (anziché in un file JavaScript transpiled), è necessario aggiornare la configurazione di Webpack. Ad esempio, in *Webpack-config. js*potrebbe essere necessario sostituire il codice seguente:

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

Per gli scenari complessi, è possibile che gli strumenti del browser (**F12**) funzionino meglio per il debug.

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>Configurare i mapping di origine usando un file tsconfig.json

Se si aggiunge al progetto un file *tsconfig.json*, Visual Studio considera la directory radice come un progetto TypeScript. Per aggiungere il file, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e quindi scegliere **Aggiungi > Nuovo elemento > Web > Script > File di configurazione JSON per TypeScript**. Viene aggiunto al progetto un file *tsconfig.json* simile al seguente.

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

* **Genera mapping di origine** (equivalente **a sourceMap** in *tsconfig. JSON*): genera il file *. map* corrispondente.
* **Specificare la directory radice dei mapping di origine** (equivalente a **MAPROOT** in *tsconfig. JSON*): specifica il percorso in cui il debugger deve trovare i file della mappa invece dei percorsi generati. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in un percorso diverso rispetto ai file con estensione js. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di mapping.
* **Specificare la directory radice dei file typescript** (equivalente a **sourceRoot** in *tsconfig. JSON*): specifica il percorso in cui il debugger deve trovare i file typescript invece dei percorsi di origine. Usare questo flag se i file di origine di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debug di JavaScript in file dinamici tramite Razor (ASP.NET)

Visual Studio supporta il debug solo per Internet Explorer e Chrome. I punti di interruzione vengono collegati automaticamente a JavaScript/TypeScript e script incorporati nei file HTML.

Il debug dei file generati dinamicamente non è automatico. Non è possibile raggiungere automaticamente i punti di interruzione nei file generati con la sintassi Razor (con estensioni cshtml, vbhtml). È possibile usare due approcci per il debug di questo tipo di file:

* **Inserire l'istruzione `debugger;` in cui si desidera interrompere**l'esecuzione. in questo modo lo script dinamico interrompe l'esecuzione e avvia il debug immediatamente durante la creazione.
* **Caricare la pagina e aprire il documento dinamico in Visual Studio**: è necessario aprire il file dinamico durante il debug, impostare il punto di interruzione e aggiornare la pagina per il funzionamento di questo metodo. Per trovare il file usare uno dei seguenti metodi, a seconda che si usi Chrome o Internet Explorer:

   Per Chrome, andare a **Esplora soluzioni > Documenti script > NomePagina**.

    > [!NOTE]
    > Se si usa Chrome è possibile che venga visualizzato un messaggio **No source is available between \<script> tags** (Nessuna origine disponibile tra i tag \<script>). Il messaggio non indica un problema ed è possibile procedere con il debug.

   In Internet Explorer, passare a **Esplora soluzioni > Documenti script > Windows Internet Explorer > NomePagina**.

Per altre informazioni, vedere [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Debug lato client di progetti ASP.NET in Google Chrome).
