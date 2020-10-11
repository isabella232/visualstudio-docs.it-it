---
title: Compilare e compilare codice TypeScript usando NuGet
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
ms.openlocfilehash: 16ff335fdf8ca76889562cfd94807ec1adc516d2
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91927926"
---
# <a name="compile-typescript-code-aspnet-core"></a>Compila codice TypeScript (ASP.NET Core)

È possibile aggiungere il supporto TypeScript ai progetti usando il TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio o tramite il pacchetto NuGet. Per i progetti sviluppati in Visual Studio 2019, si consiglia di usare TypeScript NuGet per una maggiore portabilità in diverse piattaforme e ambienti.

Per i progetti ASP.NET Core, un utilizzo comune per il pacchetto NuGet consiste nel compilare TypeScript usando il interfaccia della riga di comando di .NET Core. A meno che non si modifichi manualmente il file di progetto per importare destinazioni di compilazione da un'installazione di TypeScript SDK, il pacchetto NuGet è l'unico modo per abilitare la compilazione TypeScript usando comandi interfaccia della riga di comando di .NET Core, ad esempio `dotnet build` e `dotnet publish` . Per l' [integrazione di MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) con ASP.NET Core e typescript, scegliere anche il pacchetto NuGet sul pacchetto NPM.

## <a name="add-typescript-support-with-nuget"></a>Aggiungere il supporto TypeScript con NuGet

[Il pacchetto NuGet typescript aggiunge il](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) supporto per typescript. Quando si installa il pacchetto NuGet per TypeScript 3.2 o versione successiva nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.

Se Visual Studio è installato, il node.exe in bundle verrà automaticamente selezionato da Visual Studio. Se Node.js non è installato, si consiglia di installare la versione LTS dal sito Web di [Node.js](https://nodejs.org/en/download/) .

1. Aprire il progetto ASP.NET Core in Visual Studio.

1. In Esplora soluzioni (riquadro a destra). fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Gestisci pacchetti NuGet**. Nella scheda **Sfoglia** cercare **Microsoft. typescript. MSBuild**, quindi fare clic su **Installa** a destra per installare il pacchetto.

   ![Aggiungi pacchetto NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio aggiunge il pacchetto NuGet nel nodo **dipendenze** in Esplora soluzioni. Il riferimento al pacchetto seguente viene aggiunto al file *. csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **aggiungi > nuovo elemento**. Scegliere il **file di configurazione TYPESCRIPT JSON**e quindi fare clic su **Aggiungi**.

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
       "outDir": "wwwroot/js"
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

### <a name="build-the-application"></a>Compilare l'applicazione

1. Aggiungere i file TypeScript (*. TS*) o typescript JSX (*. TSX*) al progetto e quindi aggiungere il codice typescript. Per un semplice esempio di TypeScript, utilizzare quanto segue:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Se si usa un progetto di tipo non SDK precedente, seguire le istruzioni [riportate in rimuovere le importazioni predefinite](#remove-default-imports) prima della compilazione.

1. Scegliere **compila > Compila soluzione**.

   Sebbene l'app venga compilata automaticamente quando viene eseguita, è opportuno esaminare qualcosa che si verifica durante il processo di compilazione:

   Se sono state generate mappe di origine, aprire la cartella specificata nell'opzione *outDir* per trovare i file *. js generati insieme ai file * js. map generati.

   Per il debug sono necessari i file di mapping di origine.

1. Se si vuole eseguire la compilazione ogni volta che si salva il progetto, usare l'opzione *compileOnSave* in *. tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Per un esempio dell'uso di Gulp con l'attività Runner per compilare l'app, vedere [ASP.NET Core e typescript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Se si verificano problemi in cui Visual Studio usa una versione di Node.js o uno strumento di terze parti diverso dalla versione prevista, potrebbe essere necessario impostare il percorso di Visual Studio. Scegliere **strumenti**  >  **Opzioni**. In **progetti e soluzioni**scegliere **Web Gestione pacchetti**  >  **strumenti Web esterni**.

### <a name="run-the-application"></a>Eseguire l'applicazione

Per istruzioni su come eseguire l'app dopo la compilazione, vedere [creare la prima app Node.js](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>Dettagli della struttura dei pacchetti NuGet

`Microsoft.TypeScript.MSBuild.nupkg` contiene due cartelle principali:

- cartella di *compilazione*

    In questa cartella sono presenti due file.
    Entrambi sono punti di ingresso, rispettivamente per il file di destinazione principale TypeScript e per il file props.

    1. *Microsoft. TypeScript. MSBuild. targets*

        Questo file imposta le variabili che specificano la piattaforma di runtime, ad esempio un percorso di *TypeScript.Tasks.dll*, prima di importare *Microsoft. typescript. targets* dalla cartella *Tools* .

    2. *Microsoft. TypeScript. MSBuild. props*

        Questo file importa *Microsoft. typescript. default. props* dalla cartella *Tools* e imposta le proprietà che indicano che la compilazione è stata avviata tramite NuGet.

- cartella *strumenti*

    Le versioni del pacchetto precedenti alla 2,3 contengono solo una cartella TSC. *Microsoft. typescript. targets* e *TypeScript.Tasks.dll* si trovano a livello di radice.

    Nelle versioni del pacchetto 2,3 e versioni successive, il livello radice contiene `Microsoft.TypeScript.targets` e `Microsoft.TypeScript.Default.props` . Per ulteriori informazioni su questi file, vedere la pagina relativa alla [configurazione di MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Inoltre, la cartella contiene tre sottocartelle:

    1. *net45*

        Questa cartella contiene `TypeScript.Tasks.dll` e altre DLL da cui dipende.
        Quando si compila un progetto in una piattaforma Windows, MSBuild usa le DLL di questa cartella.

    2. *netstandard1.3*

        Questa cartella contiene un'altra versione di `TypeScript.Tasks.dll` , che viene usata per la compilazione di progetti in un computer non Windows.

    3. *TSC*

        Questa cartella contiene `tsc.js` `tsserver.js` e tutti i file di dipendenza necessari per eseguirli come script del nodo.

        > [!NOTE]
        > Se Visual Studio è installato, il *node.exe* in bundle verrà automaticamente selezionato. In caso contrario Node.js necessario che sia installato nel computer.

        Le versioni precedenti alla 3,1 contenevano un `tsc.exe` eseguibile per eseguire la compilazione. Nella versione 3,1 questa operazione è stata rimossa a favore dell'uso di `node.exe` .

### <a name="remove-default-imports"></a>Rimuovi importazioni predefinite

Nei progetti di ASP.NET Core precedenti che usano il [formato non SDK](https://docs.microsoft.com/nuget/resources/check-project-format), potrebbe essere necessario rimuovere alcuni elementi del file di progetto.

Se si usa il pacchetto NuGet per il supporto MSBuild per un progetto, il file di progetto non deve importare `Microsoft.TypeScript.Default.props` o `Microsoft.TypeScript.targets` . I file vengono importati dal pacchetto NuGet, quindi includerli separatamente può causare un comportamento imprevisto.

1. Fare clic con il pulsante destro del mouse sul progetto e scegliere **Scarica progetto**.

1. Fare clic con il pulsante destro del mouse sul progetto e scegliere **modifica \<*project file name*\> **.

   Verrà aperto il file di progetto.

1. Rimuovere i riferimenti a `Microsoft.TypeScript.Default.props` e `Microsoft.TypeScript.targets` .

   Le importazioni da rimuovere hanno un aspetto simile al seguente:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
