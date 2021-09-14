---
title: Testing unità di codice JavaScript e TypeScript
description: Visual Studio offre supporto per il testing unità di codice JavaScript e TypeScript tramite Node.js Tools for Visual Studio
ms.date: 03/18/2021
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
ms.openlocfilehash: ee04b9e3a49af86780bc9702de5d5c128dae2173
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635868"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testing unità di codice JavaScript e TypeScript in Visual Studio

È possibile scrivere ed eseguire unit test in Visual Studio usando alcuni dei framework JavaScript più diffusi senza la necessità di passare a un prompt dei comandi. Sono supportati Node.js e ASP.NET Core progetto.

I framework supportati sono:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Export Runner (questo framework è specifico di Node.js Tools for Visual Studio)

Per ASP.NET Core e JavaScript o TypeScript, vedere [Scrivere unit test per ASP.NET Core ](#write-unit-tests-for-aspnet-core).

Se un framework non è supportato, vedere [Aggiungere il supporto per un framework di unit test](#addingFramework) per informazioni sull'aggiunta del supporto.

## <a name="write-unit-tests-in-a-nodejs-project"></a>Scrivere unit test in un progetto Node.js

Prima di aggiungere unit test al progetto, verificare che il framework che si prevede di usare sia installato localmente nel progetto. La [finestra di installazione del pacchetto npm](npm-package-management.md#npmInstallWindow) semplifica questa operazione.

Il modo migliore per aggiungere unit test a un progetto consiste nel creare una cartella *tests* nel progetto e impostarla come radice del test nelle proprietà del progetto. È anche necessario selezionare il framework di test da usare.

![Impostare la radice del test e il framework di test](../javascript/media/unit-test-project-properties.png)

La finestra di dialogo **Aggiungi nuovo elemento** consente di aggiungere semplici test vuoti al progetto. Nello stesso progetto sono supportati sia JavaScript che TypeScript.

![Aggiungere un nuovo unit test](../javascript/media/unit-test-add-new-item.png)

Per uno unit test Mocha, usare il codice seguente:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Se le opzioni di unit test non sono state impostate nelle proprietà del progetto, è necessario verificare che la proprietà **Framework di test** nella finestra **Proprietà** sia impostata sul framework di test corretto per i file dello unit test. Questa operazione viene eseguita automaticamente dai modelli di file di unit test.

![Framework di test](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Le opzioni di unit test prevalgono sulle impostazioni selezionate per i singoli file.

Dopo aver aperto Esplora test (scegliere  >  **Test Windows**  >  **Esplora test),** Visual Studio individua e visualizza i test. Se inizialmente i test non vengono visualizzati, ricompilare il progetto per aggiornare l'elenco.

![Esplora test](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Per TypeScript, non usare `outdir` `outfile` l'opzione o in *tsconfig.json,* perché Esplora test non sarà in grado di trovare gli unit test.

## <a name="run-tests-nodejs"></a>Eseguire test (Node.js)

È possibile eseguire test in Visual Studio o dalla riga di comando.

### <a name="run-tests-in-visual-studio"></a>Eseguire test in Visual Studio

::: moniker range=">=vs-2019"
È possibile eseguire i test facendo clic sul collegamento **Esegui tutti** in Esplora test. In caso contrario, è possibile eseguire i test selezionando uno o più test o gruppi, facendo clic con il pulsante destro del mouse e scegliendo **Esegui** dal menu di scelta rapida. I test vengono eseguiti in background ed Esplora test aggiorna e visualizza automaticamente i risultati. È anche possibile eseguire il debug di test selezionati facendo clic con il pulsante destro del mouse e scegliendo **Debug.**
::: moniker-end
::: moniker range="vs-2017"
È possibile eseguire i test facendo clic sul collegamento **Esegui tutti** in Esplora test. Oppure è possibile eseguire i test selezionando uno o più test o gruppi, facendo clic con il pulsante destro del mouse e selezionando **Esegui test selezionati** dal menu di scelta rapida. I test vengono eseguiti in background ed Esplora test aggiorna e visualizza automaticamente i risultati. È inoltre possibile eseguire il debug di test selezionati scegliendo **Esegui debug test selezionati**.
::: moniker-end

Per TypeScript, gli unit test vengono eseguiti sul codice JavaScript generato.

> [!NOTE]
> Nella maggior parte degli scenari TypeScript è possibile eseguire il debug di un unit test impostando un punto di interruzione nel codice TypeScript, facendo clic con il pulsante destro del mouse su un test in Esplora test e scegliendo **Debug.** In scenari più complessi, ad esempio alcuni scenari che usano mappe di origine, potrebbe essere difficile raggiungere i punti di interruzione nel codice TypeScript. Come soluzione alternativa, provare a usare la parola `debugger` chiave .

> [!NOTE]
> Test di profilatura o code coverage non sono attualmente supportati.

### <a name="run-tests-from-the-command-line"></a>Eseguire test dalla riga di comando

È possibile eseguire i test [da Prompt dei comandi per gli sviluppatori per Visual Studio](../ide/reference/command-prompt-powershell.md) usando il comando seguente:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Questo comando ha un output simile al seguente:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Se si verifica un errore che indica che è impossibile trovare *vstest.console.exe*, verificare di aver aperto il prompt dei comandi per gli sviluppatori e non un prompt dei comandi normale.

## <a name="write-unit-tests-for-aspnet-core"></a>Scrivere unit test per ASP.NET Core

1. Creare un progetto ASP.NET Core e aggiungere il supporto TypeScript.

   Per un progetto di esempio, vedere [Creare un'app ASP.NET Core con TypeScript.](../javascript/tutorial-aspnet-with-typescript.md) Per il supporto degli unit test, è consigliabile iniziare con un modello di ASP.NET Core standard.

   Usare il NuGet per aggiungere il supporto TypeScript anziché il pacchetto TypeScript npm.

1. Installare il pacchetto NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/)

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto **e scegliere Scarica Project**.

   Il file *con estensione csproj* dovrebbe essere aperto in Visual Studio.

1. Aggiungere gli elementi seguenti al file *con estensione csproj* nell'elemento `PropertyGroup` .

   Questo esempio specifica Mocha come framework di test. È invece possibile specificare Jest, Tape o Jasmine.

   ```xml
   <PropertyGroup>
      ...
      <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
      <JavaScriptTestFramework>Mocha</JavaScriptTestFramework>
      <GenerateProgramFile>false</GenerateProgramFile>
   </PropertyGroup>
   ```

   `JavaScriptTestRoot`L'elemento specifica che gli unit test saranno nella cartella *tests* della radice del progetto.

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Ricarica Project**.

1. Aggiungere il supporto npm come descritto nell'articolo npm package management (Gestione dei pacchetti npm) [ASP.NET Core progetti](../javascript/npm-package-management.md#aspnet-core-projects).

   È necessario installare il runtime Node.js per il supporto npm e *aggiungere package.json* nella radice del progetto.

1. In *package.json* aggiungere il pacchetto npm desiderato nelle dipendenze.

   Ad esempio, per mocha, è possibile usare quanto segue:

   ```json
   "dependencies": {
     "mocha": "8.3.0",
   ```

   Alcuni framework di unit test, ad esempio Jest, richiedono pacchetti npm aggiuntivi. Per Jest, usare il codice JSON seguente:

   ```json
   "dependencies": {
     "jest": "26.6.3",
     "jest-editor-support": "28.1.0"
   ```

   >[!NOTE]
   > In alcuni scenari, Esplora soluzioni possibile che il nodo npm non venga visualizzato a causa di un problema noto descritto [qui.](https://github.com/aspnet/Tooling/issues/479) Se è necessario visualizzare il nodo npm, è possibile scaricare il progetto (fare clic con il pulsante destro del mouse sul progetto e scegliere **Scarica Project**) e quindi ricaricare il progetto per visualizzare nuovamente il nodo npm.

1. Aggiungere il codice da testare.

   Se si usa l'esempio descritto in Creare un'app ASP.NET Core con [TypeScript,](tutorial-aspnet-with-typescript.md)aggiungere il codice seguente alla fine del file *library.ts,* che si trova nella cartella *scripts.*

   ```typescript
   function getData(value) {
      if (value > 1) {
         return true;
      }
   }
    
   module.exports = getData;
   ```

   Per TypeScript, gli unit test vengono eseguiti sul codice JavaScript generato.

1. Aggiungere gli unit test alla cartella *tests* nella radice del progetto.

   Ad esempio, è possibile usare il codice seguente selezionando la scheda della documentazione corretta corrispondente al framework di test, in questo esempio Mocha o Jest. Questo codice verifica una funzione denominata `getData` .

   # <a name="mocha"></a>[Moka](#tab/mocha)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
   var assert = require('assert');
    
   describe('Test Suite 1', function () {
      it('getData', function () {
         assert.ok(true, getData(2));
      })
   })
   ```

   # <a name="jest"></a>[Jest](#tab/jest)

   ```typescript
   const getData = require('../wwwroot/js/library.js');
    
   test('should return true', () => {
      expect(getData(2)).toBe(true);
   });
   ```

1. Aprire Esplora test (scegliere **Test**  >  **Windows**  >  **Esplora test)** e Visual Studio individua e visualizza i test. Se inizialmente i test non vengono visualizzati, ricompilare il progetto per aggiornare l'elenco.

   ![Individuazione test in Esplora test](../javascript/media/unit-tests-aspnet-core-discovery.png)

   > [!NOTE]
   > Per TypeScript, non usare `outfile` l'opzione in *tsconfig.json* perché Esplora test non sarà in grado di trovare gli unit test. È possibile usare `outdir` l'opzione , ma assicurarsi che i file di configurazione, ad esempio `package.json` e , siano nella radice del `tsconfig.json` progetto.

## <a name="run-tests-aspnet-core"></a>Eseguire test (ASP.NET Core)

::: moniker range=">=vs-2019"
È possibile eseguire i test facendo clic sul collegamento **Esegui tutti** in Esplora test. In caso contrario, è possibile eseguire i test selezionando uno o più test o gruppi, facendo clic con il pulsante destro del mouse e scegliendo **Esegui** dal menu di scelta rapida. I test vengono eseguiti in background ed Esplora test aggiorna e visualizza automaticamente i risultati. È anche possibile eseguire il debug di test selezionati facendo clic con il pulsante destro del mouse e scegliendo **Debug.**
::: moniker-end
::: moniker range="vs-2017"
È possibile eseguire i test facendo clic sul collegamento **Esegui tutti** in Esplora test. Oppure è possibile eseguire i test selezionando uno o più test o gruppi, facendo clic con il pulsante destro del mouse e selezionando **Esegui test selezionati** dal menu di scelta rapida. I test vengono eseguiti in background ed Esplora test aggiorna e visualizza automaticamente i risultati. È inoltre possibile eseguire il debug di test selezionati scegliendo **Esegui debug test selezionati**.
::: moniker-end

Per TypeScript, gli unit test vengono eseguiti sul codice JavaScript generato.

![Risultati di Esplora test](../javascript/media/unit-tests-aspnet-core-run.png)

> [!NOTE]
> Nella maggior parte degli scenari TypeScript è possibile eseguire il debug di un unit test impostando un punto di interruzione nel codice TypeScript, facendo clic con il pulsante destro del mouse su un test in Esplora test e scegliendo **Debug.** In scenari più complessi, ad esempio alcuni scenari che usano mappe di origine, potrebbe essere difficile raggiungere i punti di interruzione nel codice TypeScript. Come soluzione alternativa, provare a usare la parola `debugger` chiave .

> [!NOTE]
> Test di profilatura o code coverage non sono attualmente supportati.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Aggiungere il supporto per un framework di unit test

È possibile aggiungere il supporto per altri framework di test implementando la logica di individuazione ed esecuzione tramite JavaScript. A questo scopo, aggiungere una cartella con il nome del framework di test in:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Questa cartella deve contenere un file JavaScript con lo stesso nome che esporta le due funzioni seguenti:

* `find_tests`
* `run_tests`

Per un buon esempio delle implementazioni `find_tests` e `run_tests`, vedere l'implementazione per il framework di unit test Mocha in:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

L'individuazione dei framework di test disponibili avviene all'avvio di Visual Studio. Se un framework viene aggiunto mentre Visual Studio è in esecuzione, riavviare Visual Studio per rilevare il framework. Il riavvio non è tuttavia necessario quando si apportano modifiche all'implementazione.

## <a name="unit-tests-in-net-framework"></a>Unit test in .NET Framework

Non si è limitati alla scrittura di unit test solo nei progetti Node.js e ASP.NET Core progetto. Quando si aggiungono le proprietà TestFramework e TestRoot a un qualsiasi progetto C# o Visual Basic, questi test vengono enumerati e possono essere eseguiti tramite la finestra Esplora Test.

A tale scopo, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni, scegliere **Scarica progetto**, quindi scegliere **Edit Project** (Modifica progetto). Nel file di progetto aggiungere i due elementi seguenti a un gruppo di proprietà.

> [!IMPORTANT]
> Assicurarsi che il gruppo di proprietà al quale vengono aggiunti gli elementi non abbia una condizione specifica,
> che potrebbe causare comportamenti inaspettati.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Successivamente, aggiungere i test alla cartella radice di test specificata. A questo punto i test saranno disponibili per essere eseguiti nella finestra Esplora test. Se inizialmente non vengono visualizzati, potrebbe essere necessario ricompilare il progetto.

## <a name="unit-test-net-core-and-net-standard"></a>Unit test .NET Core e .NET Standard

Oltre alle proprietà precedenti, è anche necessario installare il pacchetto NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) e impostare la proprietà :

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Alcuni framework di test possono richiedere pacchetti npm aggiuntivi per il rilevamento dei test. Ad esempio, jest richiede il pacchetto npm jest-editor-support. Se necessario, consultare la documentazione per il framework specifico.
