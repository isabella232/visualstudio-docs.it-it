---
title: Eseguire il debug di un'app Node.js
description: Visual Studio offre supporto per il debug di applicazioni Node.js in Visual Studio
ms.custom: ''
ms.date: 12/03/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 57054d8ba804a653b11b05fc229fa162d677bcae
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803781"
---
# <a name="debug-a-nodejs-app-in-visual-studio"></a>Eseguire il debug di un'app Node.js in Visual Studio

È possibile eseguire il debug di codice JavaScript e TypeScript con Visual Studio. È possibile impostare e raggiungere punti di interruzione, collegare il debugger, esaminare variabili, visualizzare lo stack di chiamate e usare altre funzionalità di debug.

## <a name="debug-server-side-script"></a>Eseguire il debug di script lato server

1. Con il progetto aperto in Visual Studio, aprire un file JavaScript lato server (ad esempio *server.js*) e fare clic nella barra di navigazione sinistra per impostare un punto di interruzione:

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    I punti di interruzione rappresentano la funzionalità di base essenziale per un debug affidabile. Un punto di interruzione indica il punto in cui Visual Studio dovrebbe sospendere l'esecuzione del codice in modo da poter esaminare i valori delle variabili, il comportamento della memoria o lo stato di esecuzione di un ramo del codice.

1. Per eseguire l'app premere **F5** (**Debug** > **Avvia debug**).

    Il debugger sospende l'esecuzione nel punto di interruzione impostato (l'istruzione corrente è contrassegnata in giallo). A questo punto è possibile controllare lo stato dell'app passando il mouse sulle variabili attualmente incluse nell'ambito e usando finestre del debugger come **Variabili locali** e **Espressioni di controllo**.

1. Premere **F5** per continuare con l'esecuzione dell'app.

1. Per usare Chrome Developer Tools o gli Strumenti F12, premere **F12**. È possibile usare questi strumenti per esaminare il modello DOM e interagire con l'app mediante la console JavaScript.

## <a name="debug-client-side-script"></a>Debug di script lato client

Visual Studio supporta il debug solo per Internet Explorer e Chrome. In alcuni scenari il debugger raggiunge automaticamente i punti di interruzione nel codice JavaScript e TypeScript e negli script incorporati nei file HTML.

Se l'origine è minimizzata o creata da un transpiler come TypeScript o Babel, è necessario usare [mapping di origine](#generate_sourcemaps) per ottenere la migliore esperienza di debug. Senza i mapping di origine, è comunque possibile collegare il debugger a uno script lato client in esecuzione. Tuttavia in molti casi è possibile impostare e raggiungere punti di interruzione solo nel file minimizzato o convertito tramite transpiler, e non nel file di origine. Ad esempio, in un'app Vue.js lo script minimizzato viene passato come stringa a un'istruzione `eval` e l'esecuzione efficace del codice istruzione per istruzione con il debugger di Visual Studio è possibile solo se si usano i mapping di origine. In alcuni scenari di debug complessi è anche possibile usare i Chrome Developer Tools o gli Strumenti F12 per Microsoft Edge.

Per il collegamento del debugger da Visual Studio e l'accesso a punti di interruzione nel codice lato client, in genere il debugger necessita aiuto per identificare il processo corretto. Di seguito viene descritto un metodo per abilitare questa funzionalità tramite Chrome.

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>Collegare il debugger a script lato client con Chrome

1. Chiudere tutte le finestre di Chrome.

    Questa operazione è necessaria per poter avviare Chrome in modalità di debug.

2. Aprire il comando **Esegui** dal pulsante **Start** di Windows (fare clic con il pulsante destro del mouse e scegliere **Esegui**) e immettere il comando seguente:

    `chrome.exe --remote-debugging-port=9222`

    Chrome viene avviato con il debug abilitato.

3. Passare a Visual Studio e impostare un punto di interruzione nel codice sorgente. Impostare il punto di interruzione in una riga di codice che consente i punti di interruzione, ad esempio un'istruzione `return` o una dichiarazione `var`.

    ![Imposta punto di interruzione](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    Se è necessario trovare codice specifico in un file generato di grandi dimensioni, usare **CTRL**+**F** (**Modifica** > **Trova e sostituisci** > **Ricerca veloce**).

4. Con Chrome selezionato come destinazione di debug in Visual Studio, premere **CTRL**+**F5** (**Debug** > **Avvia senza eseguire debug**) per eseguire l'app nel browser.

    L'app viene aperta in una nuova scheda del browser.

    Se Chrome è disponibile nel computer in uso ma non viene visualizzato come opzione, scegliere **Esplora con** dall'elenco a discesa delle destinazioni di debug e selezionare Chrome come destinazione browser predefinita (scegliere **Imposta come predefinito**).

5. Scegliere **Debug** > **Associa a processo**.

6. Nella finestra di dialogo **Associa a processo** scegliere **Webkit code** (Codice WebKit) nel campo **Attach to** (Associa a), quindi digitare **chrome** nella casella del filtro per applicare un filtro ai risultati della ricerca.

    **Webkit code** (Codice WebKit) è il valore richiesto per Chrome, che è un browser basato su WebKit.

7. Selezionare il processo di Chrome con la porta host corretta (in questa immagine 1337) e selezionare **Associa**.

    ![Associa a processo](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    Se DOM Explorer e la console JavaScript Console si aprono in Visual Studio, il debugger è stato associato correttamente. Questi strumenti di debug sono simili ai Chrome Developer Tools e agli Strumenti F12 per Microsoft Edge.

    > [!NOTE]
    > Se il debugger non è associato e viene visualizzato il messaggio "Impossibile connettersi al processo. Operazione non valida nello stato corrente", usare Gestione attività per chiudere tutte le istanze di Chrome prima di avviare Chrome in modalità di debug. Se sono in esecuzione estensione di Chrome, la modalità di debug complete potrebbe essere impedita.

8. Se il codice con il punto di interruzione è già stato eseguito, aggiornare la pagina del browser per raggiungere il punto di interruzione.

    Durante la pausa del debugger, è possibile esaminare lo stato dell'app passando il mouse sulle variabili e usando le finestre del debugger. È possibile far avanzare il debugger eseguendo il codice istruzione per istruzione (**F5**, **F10** e **F11**).

    Per codice JavaScript minimizzato o convertito tramite transpile, è possibile raggiungere il punto di interruzione sia nel codice JavaScript convertito tramite transpile sia nella posizione corrispondente mappata nel file TypeScript (mediante mapping di origine), a seconda dell'ambiente e dello stato del browser. In entrambi i casi è possibile eseguire il codice istruzione per istruzione ed esaminare le variabili.

    * Se è necessario inserire un'interruzione nel codice in un file TypeScript ma non si riesce a eseguire questa operazione, usare **Associa a processo** come descritto nei passaggi precedenti per associare il debugger. Quindi aprire il file di TypeScript generato dinamicamente da Esplora soluzioni selezionando **Documenti script** > **filename.tsx**, impostare un punto di interruzione e aggiornare la pagina nel browser. Impostare il punto di interruzione in una riga di codice che ammette i punti di interruzione, come l'istruzione `return` o una dichiarazione `var`.

        Oppure, se è necessario inserire un'interruzione nel codice in un file TypeScript ma non si riesce a eseguire questa operazione, provare a usare l'istruzione `debugger;` nel file TypeScript oppure impostare i punti di interruzione in Chrome Developer Tools.

    * Se è necessario inserire un'interruzione nel codice in un file JavaScript sottoposto a transpile, ad esempio *app bundle.js*, ma non si riesce a eseguire questa operazione, rimuovere il file del mapping di origine *filename.js.map*.

     > [!TIP]
     > Dopo aver eseguito per la prima volta l'associazione al processo seguendo questa procedura, è possibile ripetere rapidamente l'associazione allo stesso processo in Visual Studio 2017 scegliendo **Debug** > **Riassocia a processo**.

## <a name="generate_sourcemaps"></a> Generare mapping di origine per il debug

Visual Studio è in grado di usare e generare mapping di origine su file di origine JavaScript. Questo è spesso necessario se l'origine è minimizzata o creata da un transpiler come Babel o TypeScript. Le opzioni disponibili dipendono dal tipo di progetto.

* Per impostazione predefinita, un progetto TypeScript in Visual Studio genera mapping di origine.

* In un progetto JavaScript è necessario generare mapping di origine usando un bundler come webpack e un compilatore, ad esempio il compilatore TypeScript (o Babel), che può essere aggiunto al progetto. Per il compilatore TypeScript è necessario aggiungere anche un file *tsconfig.json*. Per un esempio che illustra come eseguire questa operazione usando una configurazione webpack di base, vedere [Creare un'app Node.js con React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

> [!NOTE]
> Se non si ha familiarità con i mapping di origine, prima di continuare leggere [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (Presentazione dei mapping di origine di JavaScript).

Per configurare le impostazioni avanzate per i mapping di origine, usare un file *tsconfig.json* o le impostazioni progetto in un progetto TypeScript, ma non entrambi.

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

* **inlineSourceMap**: crea un file unico con mapping di origine invece di creare un mapping di origine separato per ogni file di origine.
* **inlineSources**: include l'origine e i mapping di origine in un unico file; richiede l'impostazione di *inlineSourceMap* o di *sourceMap*.
* **mapRoot**: specifica il percorso in cui il debugger trova il file del mapping di origine (con estensione *map*) in alternativa al percorso predefinito. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in una posizione diversa rispetto ai file con estensione *js*. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file con estensione *map*.
* **sourceMap**: genera un file con estensione *map* corrispondente.
* **sourceRoot**: specifica il percorso in cui il debugger trova i file TypeScript in alternativa ai percorsi predefiniti. Usare questo flag se le origini di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

Per altri dettagli sulle opzioni del compilatore, vedere la pagina [Opzioni del compilatore](https://www.typescriptlang.org/docs/handbook/compiler-options.html) nel manuale di TypeScript.

### <a name="configure-source-maps-using-project-settings"></a>Configurare i mapping di origine usando le impostazioni di progetto

È anche possibile configurare le impostazioni di mapping di origine usando le proprietà del progetto, facendo clic con il pulsante destro del mouse sul progetto e quindi scegliendo **Progetto > Proprietà > Compilazione TypeScript > Debug**.

Sono disponibili le impostazioni del progetto seguenti.

* **Genera mapping di origine** (equivalente a **sourceMap** in *tsconfig.json*): genera il file con estensione *map* corrispondente.
* **Specifica la directory radice dei mapping di origine** (equivalente a **mapRoot** in *tsconfig.json*): specifica il percorso in cui il debugger trova i file di mapping in alternativa ai percorsi predefiniti. Usare questo flag se i file di runtime con estensione *map* devono trovarsi in un percorso diverso rispetto ai file con estensione js. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di mapping.
* **Specifica la directory radice dei file TypeScript** (equivalente a **sourceRoot** in *tsconfig.json*): specifica il percorso in cui il debugger trova i file TypeScript in alternativa ai percorsi predefiniti. Usare questo flag se i file di origine di runtime devono trovarsi in un percorso diverso rispetto a quello usato per la fase di progettazione. Il percorso specificato è incorporato nel mapping di origine per indirizzare il debugger alla posizione dei file di origine.

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>Debug di JavaScript in file dinamici tramite Razor (ASP.NET)

Visual Studio supporta il debug solo per Internet Explorer e Chrome. I punti di interruzione vengono collegati automaticamente a JavaScript/TypeScript e script incorporati nei file HTML.

Il debug dei file generati dinamicamente non è automatico. Non è possibile raggiungere automaticamente i punti di interruzione nei file generati con la sintassi Razor (con estensioni cshtml, vbhtml). È possibile usare due approcci per il debug di questo tipo di file:

* **Posizionare l'istruzione `debugger;` dove si vuole inserire l'interruzione**: in questo modo lo script dinamico arresta l'esecuzione e avvia immediatamente il debug durante la creazione.
* **Caricare la pagina e aprire il documento dinamico in Visual Studio**: per il funzionamento di questo metodo è necessario aprire il file dinamico durante il debug, impostare il punto di interruzione e aggiornare la pagina. Per trovare il file usare uno dei seguenti metodi, a seconda che si usi Chrome o Internet Explorer:

   Per Chrome, andare a **Esplora soluzioni > Documenti script > NomePagina**.

    > [!NOTE]
    > Se si usa Chrome, potrebbe essere visualizzato un messaggio `no source is available between `<script>` tags.` This is OK, just continue debugging.

   In Internet Explorer, passare a **Esplora soluzioni > Documenti script > Windows Internet Explorer > NomePagina**.

Per altre informazioni, vedere [Client-side debugging of ASP.NET projects in Google Chrome](https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Debug lato client di progetti ASP.NET in Google Chrome).
