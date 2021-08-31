---
title: Compilare e compilare codice TypeScript con npm
description: Informazioni su come aggiungere il supporto TypeScript ai progetti Visual Studio usando node Gestione pacchetti (npm).
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1a3426b4e8d7dae3b7585a47dca9e98a8cbc14a6
ms.sourcegitcommit: 409a750a944a72c5931f6094deb4dc9a2635a984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123262088"
---
# <a name="compile-typescript-code-nodejs"></a>Compilare codice TypeScript (Node.js)

È possibile aggiungere il supporto TypeScript ai progetti usando il TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio o usando npm. Per i progetti sviluppati in Visual Studio 2019, è necessario usare il pacchetto npm TypeScript per una maggiore portabilità tra piattaforme e ambienti diversi.

Per ASP.NET Core progetti, è consigliabile usare il NuGet [pacchetto.](../javascript/compile-typescript-code-nuget.md)

## <a name="add-typescript-support-using-npm"></a>Aggiungere il supporto TypeScript con npm

Il [pacchetto npm TypeScript aggiunge](https://www.npmjs.com/package/typescript) il supporto TypeScript. Quando il pacchetto npm per TypeScript 2.1 o versione successiva è installato nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.

1. [Seguire le istruzioni](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json) per installare il carico Node.js di sviluppo e il Node.js runtime.

   Per l'integrazione più semplice con Visual Studio, creare il progetto usando uno dei modelli TypeScript Node.js, ad esempio il modello Blank Node.js Web Application. In caso contrario, usare un Node.js JavaScript incluso in Visual Studio e seguire le istruzioni qui oppure usare un [progetto Apri](../javascript/develop-javascript-code-without-solutions-projects.md) cartella.

1. Se il progetto non lo include già, installare il pacchetto [npm TypeScript](https://www.npmjs.com/package/typescript).

   Dal Esplora soluzioni (riquadro destro) aprire ilpackage.js *nella* radice del progetto. I pacchetti elencati corrispondono ai pacchetti nel nodo npm in Esplora soluzioni. Per altre informazioni, vedere [Gestire i pacchetti npm](../javascript/npm-package-management.md).

   Per un Node.js, è possibile installare il pacchetto npm TypeScript tramite la riga di comando o l'IDE. Per eseguire l'installazione usando l'IDE, fare clic con il pulsante destro del mouse sul nodo npm in Esplora soluzioni, scegliere Installa nuovo **pacchetto npm,** cercare **TypeScript** e installare il pacchetto.

   Selezionare **l'opzione npm** nella finestra **Output** per visualizzare lo stato di avanzamento dell'installazione del pacchetto. Il pacchetto installato viene visualizzato nel **nodo npm** in Esplora soluzioni.

1. Se il progetto non lo include già, aggiungere un file con estensione *tsconfig* alla radice del progetto. Per aggiungere il file, fare clic con il pulsante destro del mouse sul nodo del progetto **e scegliere Aggiungi > nuovo elemento**. Scegliere il **file di configurazione JSON TypeScript** e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge il *tsconfig.jsfile* alla radice del progetto. È possibile usare questo file per [configurare le opzioni per](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) il compilatore TypeScript.

1. Aprire *tsconfig.jse* aggiornare per impostare le opzioni del compilatore desiderate.

   Di seguito è riportato un esempio di una semplice *tsconfig.jssu* file.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Esempio:
   - *include* indica al compilatore dove trovare i file TypeScript (*.ts).
   - *L'opzione outDir* specifica la cartella di output per i file JavaScript semplici traslittati dal compilatore TypeScript.
   - *l'opzione sourceMap* indica se il compilatore genera *file sourceMap.*

   La configurazione precedente fornisce solo un'introduzione di base alla configurazione di TypeScript. Per informazioni su altre opzioni, vederetsconfig.js[ su](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Compilare l'applicazione

1. Aggiungere i file TypeScript (*.ts*) o TypeScript JSX (*.tsx*) al progetto e quindi aggiungere il codice TypeScript. Per un semplice esempio di TypeScript, usare quanto segue:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. In *package.jssu*, aggiungere il supporto per Visual Studio comandi di compilazione e pulizia usando gli script seguenti.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Se è necessario compilare usando uno strumento di terze parti come webpack, è possibile aggiungere uno script di compilazione della riga di comando alpackage.js *file:*

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Per un esempio di uso di webpack con React e un file di configurazione webpack, vedere Creare [un'app Web](../javascript/tutorial-nodejs-with-react-and-jsx.md)con Node.js e React .

   Per un esempio di uso di Vue.js con TypeScript, vedere [Creare un'Vue.js app.](/javascript/create-application-with-vuejs)

1. Se è necessario configurare opzioni come la pagina di avvio, il percorso del runtime di Node.js, la porta dell'applicazione o gli argomenti di runtime, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Proprietà**.

   >[!NOTE]
   > Quando si configurano strumenti di terze parti, Node.js i percorsi configurati in Strumenti Opzioni Progetti e soluzioni Web Gestione pacchetti  >    >    >    >  **Strumenti Web esterni**. Queste impostazioni vengono usate per altri tipi di progetto.

1. Scegliere **Compila > compila soluzione**.

   Anche se l'app viene compilata automaticamente quando viene eseguita, è necessario esaminare qualcosa che si verifica durante il processo di compilazione:

   Se sono stati generati mapping di origine, aprire la cartella specificata nell'opzione *outDir* e trovare i file.js generati insieme ai \* file \* js.map generati.

   I file della mappa di origine sono necessari per il [debug di](../javascript/debug-nodejs.md).

### <a name="run-the-application"></a>Eseguire l'applicazione

Per istruzioni su come eseguire l'app dopo la compilazione, vedere [Creare la prima](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json#run-the-app)app Node.js app .

## <a name="automate-build-tasks"></a>Automatizzare le attività di compilazione

È possibile usare Task Runner Explorer in Visual Studio per automatizzare le attività per strumenti di terze parti come npm e webpack.

- [NPM Task Runner:](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) aggiunge il supporto per gli script npm definiti in *package.jsin*. Supporta yarn.
- [Webpack Task Runner:](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) aggiunge il supporto per webpack.
