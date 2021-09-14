---
title: Compilare e compilare codice TypeScript usando NuGet
description: Informazioni su come aggiungere il supporto TypeScript ai progetti Visual Studio usando il pacchetto NuGet.
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
ms.openlocfilehash: 1bf1deb271d7a20527f53260813e35e0de9daa19
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625794"
---
# <a name="compile-typescript-code-aspnet-core"></a>Compilare codice TypeScript (ASP.NET Core)

È possibile aggiungere il supporto TypeScript ai progetti usando il TypeScript SDK, disponibile per impostazione predefinita nel programma di installazione di Visual Studio o usando il NuGet. Per i progetti sviluppati Visual Studio 2019, si consiglia di usare l'NuGet TypeScript per una maggiore portabilità tra piattaforme e ambienti diversi.

Per ASP.NET Core, un utilizzo comune per il pacchetto NuGet è la compilazione di TypeScript usando il interfaccia della riga di comando di .NET Core. A meno che il file di progetto non venga modificato manualmente per importare destinazioni di compilazione da un'installazione di TypeScript SDK, il pacchetto NuGet è l'unico modo per abilitare la compilazione TypeScript usando comandi interfaccia della riga di comando di .NET Core come `dotnet build` e `dotnet publish` . Inoltre, per [MSBuild'integrazione](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) con ASP.NET Core e TypeScript, scegliere il pacchetto NuGet pacchetto rispetto al pacchetto npm.

## <a name="add-typescript-support-with-nuget"></a>Aggiungere il supporto di TypeScript con NuGet

[Il pacchetto di NuGet TypeScript aggiunge](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) il supporto TypeScript. Quando si installa il pacchetto NuGet per TypeScript 3.2 o versione successiva nel progetto, la versione corrispondente del servizio di linguaggio TypeScript viene caricata nell'editor.

Se Visual Studio installato, il node.exe in bundle verrà automaticamente prelevato dal Visual Studio. Se non è installata una Node.js, è consigliabile installare la versione LTS dal sito [WebNode.js.](https://nodejs.org/en/download/)

1. Aprire il progetto ASP.NET Core in Visual Studio.

1. In Esplora soluzioni (riquadro destro). Fare clic con il pulsante destro del mouse sul nodo **del progetto e scegliere Gestisci NuGet pacchetti**. Nella scheda **Sfoglia** cercare **Microsoft.TypeScript.MSBuild** e quindi  fare clic su Installa a destra per installare il pacchetto.

   ![Aggiungere NuGet pacchetto](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio aggiunge il pacchetto NuGet nel **nodo Dipendenze** in Esplora soluzioni. Il riferimento al pacchetto seguente viene aggiunto al file con estensione csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Fare clic con il pulsante destro del mouse sul nodo **del progetto e scegliere > Nuovo elemento**. Scegliere il **file di configurazione JSON TypeScript** e quindi fare clic su **Aggiungi.**

   Visual Studio aggiunge il file *tsconfig.json* alla radice del progetto. È possibile usare questo file per [configurare le opzioni per](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) il compilatore TypeScript.

1. Aprire *tsconfig.json e* aggiornare per impostare le opzioni del compilatore desiderate.

   Di seguito è riportato un esempio di un semplice file *tsconfig.json.*

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
   - *include* indica al compilatore dove trovare i file TypeScript (*.ts).
   - *L'opzione outDir* specifica la cartella di output per i file JavaScript semplici che vengono transpiled dal compilatore TypeScript.
   - *L'opzione sourceMap* indica se il compilatore genera *file sourceMap.*

   La configurazione precedente fornisce solo un'introduzione di base alla configurazione di TypeScript. Per informazioni su altre opzioni, vedere [tsconfig.json.](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

### <a name="build-the-application"></a>Compilare l'applicazione

1. Aggiungere i file TypeScript (*.ts*) o TypeScript JSX (*.tsx*) al progetto e quindi aggiungere il codice TypeScript. Per un semplice esempio di TypeScript, usare quanto segue:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Se si usa un progetto di tipo non SDK precedente, seguire le istruzioni in [Rimuovere le importazioni predefinite](#remove-default-imports) prima della compilazione.

1. Scegliere **Compila > Compila soluzione.**

   Anche se l'app viene compilata automaticamente quando viene eseguita, è necessario esaminare un evento che si verifica durante il processo di compilazione:

   Se sono stati generati mapping di origine, aprire la cartella specificata nell'opzione *outDir* per trovare i file *.js generati insieme ai file *js.map generati.

   I file della mappa di origine sono necessari per il debug.

1. Se si vuole eseguire la compilazione ogni volta che si salva il progetto, usare *l'opzione compileOnSave* in *.tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Per un esempio dell'uso di gulp con Task Runner per compilare l'app, vedere ASP.NET Core [e TypeScript.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

Se si verificano problemi in cui Visual Studio usa una versione di Node.js o uno strumento di terze parti diverso da quello previsto, potrebbe essere necessario impostare il percorso per l'uso di Visual Studio. Scegliere **Strumenti**  >  **Opzioni**. In **Progetti e soluzioni** scegliere Web **Gestione pacchetti** Strumenti  >  **Web esterni.**

### <a name="run-the-application"></a>Eseguire l'applicazione

Per istruzioni su come eseguire l'app dopo la compilazione, vedere [Creare la prima app Node.js app](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>NuGet della struttura del pacchetto

`Microsoft.TypeScript.MSBuild.nupkg` contiene due cartelle principali:

- *cartella build*

    In questa cartella si trovano due file.
    Entrambi sono punti di ingresso, rispettivamente per il file di destinazione TypeScript principale e il file props.

    1. *Microsoft.TypeScript. MSBuild.targets*

        Questo file imposta le variabili che specificano la piattaforma *di* run-time, ad esempio un percorsoTypeScript.Tasks.dll, prima di *importare Microsoft.TypeScript.targets* dalla *cartella tools.*

    2. *Microsoft.TypeScript. MSBuild.props*

        Questo file importa *Microsoft.TypeScript.Default.props* dalla cartella *tools* e imposta le proprietà che indicano che la compilazione è stata avviata tramite NuGet.

- *cartella tools*

    Le versioni dei pacchetti precedenti alla 2.3 contengono solo una cartella tsc. *Microsoft.TypeScript.targets* *eTypeScript.Tasks.dll* si trovano al livello radice.

    Nelle versioni del pacchetto 2.3 e successive il livello radice contiene `Microsoft.TypeScript.targets` e `Microsoft.TypeScript.Default.props` . Per altre informazioni su questi file, vedere [MSBuild Configuration](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Inoltre, la cartella contiene tre sottocartelle:

    1. *net45*

        Questa cartella `TypeScript.Tasks.dll` contiene e altre DLL da cui dipende.
        Quando si compila un progetto in una Windows, MSBuild usa le DLL di questa cartella.

    2. *netstandard1.3*

        Questa cartella contiene un'altra versione di , che viene usata durante la compilazione di progetti in un `TypeScript.Tasks.dll` computer non Windows distribuzione.

    3. *Tsc*

        Questa cartella contiene `tsc.js` e tutti i file di dipendenza necessari per `tsserver.js` eseguirli come script del nodo.

        > [!NOTE]
        > Se Visual Studio installato, ilnode.exe *in* bundle verrà prelevato automaticamente. In Node.js deve essere installato nel computer.

        Le versioni precedenti alla 3.1 contenevano un `tsc.exe` eseguibile per eseguire la compilazione. Nella versione 3.1 questa funzionalità è stata rimossa a favore dell'uso di `node.exe` .

### <a name="remove-default-imports"></a>Rimuovere le importazioni predefinite

Nei progetti ASP.NET Core che usano [il formato non di tipo SDK](/nuget/resources/check-project-format), potrebbe essere necessario rimuovere alcuni elementi del file di progetto.

Se si usa il pacchetto NuGet per MSBuild per un progetto, il file di progetto non deve `Microsoft.TypeScript.Default.props` importare o `Microsoft.TypeScript.targets` . I file vengono importati dal pacchetto NuGet, quindi includerli separatamente può causare un comportamento imprevisto.

1. Fare clic con il pulsante destro del mouse sul progetto **e scegliere Scarica Project**.

1. Fare clic con il pulsante destro del mouse sul progetto e **scegliere Modifica. \<*project file name*\>**

   Verrà aperto il file di progetto.

1. Rimuovere i riferimenti `Microsoft.TypeScript.Default.props` a e `Microsoft.TypeScript.targets` .

   Le importazioni da rimuovere sono simili alle seguenti:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
