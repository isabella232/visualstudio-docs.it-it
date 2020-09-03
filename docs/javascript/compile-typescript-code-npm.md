---
title: Compilare e compilare codice TypeScript con NPM
description: Informazioni su come compilare e compilare TypeScript in Visual Studio.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 58603db021d7aeebe3272711e5ba92d96eb22075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250169"
---
# <a name="compile-typescript-code-nodejs"></a>Compila codice TypeScript (Node.js)

È possibile aggiungere il supporto TypeScript ai progetti usando il TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio o tramite NPM. Per i progetti sviluppati in Visual Studio 2019, si consiglia di usare il pacchetto NPM TypeScript per una maggiore portabilità in diversi ambienti e piattaforme.

Per ASP.NET Core progetti, è consigliabile usare invece il [pacchetto NuGet](../javascript/compile-typescript-code-nuget.md) .

## <a name="add-typescript-support-using-npm"></a>Aggiungere il supporto TypeScript con NPM

Il [pacchetto NPM typescript](https://www.npmjs.com/package/typescript) aggiunge il supporto per typescript. Quando il pacchetto npm per TypeScript 2.1 o versione successiva è installato nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.

1. [Seguire le istruzioni](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json) per installare il carico di lavoro di sviluppo Node.js e il Node.js Runtime.

   Per l'integrazione più semplice con Visual Studio, creare il progetto usando uno dei modelli di Node.js TypeScript, ad esempio il modello di applicazione Web Node.js vuota. In caso contrario, usare un modello Node.js JavaScript incluso in Visual Studio e seguire le istruzioni riportate in questo documento oppure usare un progetto di [cartella aperta](../javascript/develop-javascript-code-without-solutions-projects.md) .

1. Se il progetto non lo include già, installare il [pacchetto NPM typescript](https://www.npmjs.com/package/typescript).

   Da Esplora soluzioni (riquadro a destra) aprire il *package.js* nella radice del progetto. I pacchetti elencati corrispondono ai pacchetti nel nodo NPM in Esplora soluzioni. Per altre informazioni, vedere [gestire i pacchetti NPM](../javascript/npm-package-management.md).

   Per un progetto di Node.js, è possibile installare il pacchetto NPM TypeScript usando la riga di comando o l'IDE. Per eseguire l'installazione usando l'IDE, fare clic con il pulsante destro del mouse sul nodo NPM in Esplora soluzioni, scegliere **Installa nuovo pacchetto NPM**, cercare **typescript**e installare il pacchetto.

   Selezionare l'opzione **NPM** nella finestra **output** per visualizzare lo stato di avanzamento dell'installazione del pacchetto. Il pacchetto installato viene visualizzato sotto il nodo **NPM** in Esplora soluzioni.

1. Se il progetto non lo include già, aggiungere un file con *estensione tsconfig* alla radice del progetto. Per aggiungere il file, fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **aggiungi > nuovo elemento**. Scegliere il **file di configurazione TYPESCRIPT JSON**e quindi fare clic su **Aggiungi**.

   Visual Studio aggiunge il *tsconfig.jsnel* file alla radice del progetto. È possibile usare questo file per [configurare le opzioni](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) per il compilatore typescript.

1. Aprire *tsconfig.json* e aggiornare per impostare le opzioni del compilatore desiderate.

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
   - *include* indica al compilatore dove trovare i file typescript (*. TS).
   - l'opzione *outDir* specifica la cartella di output per i file JavaScript semplici che vengono traspilati dal compilatore typescript.
   - l'opzione *sourceMap* indica se il compilatore genera file *sourceMap* .

   La configurazione precedente fornisce solo un'introduzione di base alla configurazione di TypeScript. Per informazioni su altre opzioni, vedere [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="build-the-application"></a>Compilare l'applicazione

1. Aggiungere i file TypeScript (*. TS*) o typescript JSX (*. TSX*) al progetto e quindi aggiungere il codice typescript. Per un semplice esempio di TypeScript, utilizzare quanto segue:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. In *package.js*, aggiungere il supporto per la compilazione e la pulizia dei comandi di Visual Studio usando gli script seguenti.

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   Se è necessario eseguire la compilazione usando uno strumento di terze parti come Webpack, è possibile aggiungere uno script di compilazione da riga di comando all' *package.jsnel* file:

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   Per un esempio dell'uso di Webpack con React e di un file di configurazione di Webpack, vedere [creare un'app Web con Node.js e React](../javascript/tutorial-nodejs-with-react-and-jsx.md).

   Per un esempio dell'uso di Vue.js con TypeScript, vedere [creare un'applicazione Vue.js](/javascript/create-application-with-vuejs).

1. Se è necessario configurare opzioni come la pagina di avvio, il percorso della Node.js Runtime, la porta dell'applicazione o gli argomenti di runtime, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni e scegliere **Proprietà**.

   >[!NOTE]
   > Quando si configurano gli strumenti di terze parti, i progetti Node.js non utilizzano i percorsi configurati in **strumenti**  >  **Opzioni**  >  **progetti e soluzioni**  >  **Web Gestione pacchetti**  >  **strumenti Web esterni**. Queste impostazioni vengono usate per altri tipi di progetto.

1. Scegliere **compila > Compila soluzione**.

   Sebbene l'app venga compilata automaticamente quando viene eseguita, è opportuno esaminare qualcosa che si verifica durante il processo di compilazione:

   Se sono state generate mappe di origine, aprire la cartella specificata nell'opzione *outDir* per trovare i \* file con estensione js generati insieme ai \* file js. map generati.

   Per il [debug](../javascript/debug-nodejs.md)sono necessari i file di mapping di origine.

## <a name="automate-build-tasks"></a>Automatizzare le attività di compilazione

Per automatizzare le attività di strumenti di terze parti come NPM e Webpack, è possibile usare Esplora attività in Visual Studio.

- [Attività Runner di NPM](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) : aggiunge il supporto per gli script NPM definiti in *package.json*. Supporta Yarn.
- [Webpack Task Runner](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) : aggiunge il supporto per Webpack.
