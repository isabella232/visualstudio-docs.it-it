---
title: Testing unità di codice JavaScript e TypeScript
description: Visual Studio offre supporto per il testing unità di codice JavaScript e TypeScript tramite Node.js Tools for Visual Studio
ms.date: 07/06/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e10f9b628d1d9fbbdb2911977fe7e63b1a7b6d57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957478"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testing unità di codice JavaScript e TypeScript in Visual Studio

Node.js Tools For Visual Studio consente di scrivere ed eseguire unit test usando alcuni dei più diffusi framework JavaScript senza la necessità di passare a un prompt dei comandi.

I framework supportati sono:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))
* Export Runner (questo framework è specifico di Node.js Tools for Visual Studio)

Se un framework non è supportato, vedere [Aggiungere il supporto per un framework di unit test](#addingFramework) per informazioni sull'aggiunta del supporto.

## <a name="write-unit-tests"></a>Scrivere unit test

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

Dopo l'apertura di Esplora test (scegliere **test**  >    >  **Esplora test** di Windows), Visual Studio individua e Visualizza i test. Se inizialmente i test non vengono visualizzati, ricompilare il progetto per aggiornare l'elenco.

![Esplora test](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Per TypeScript, non usare l' `outdir` opzione o `outfile` in *tsconfig.json*, perché Esplora test non sarà in grado di trovare gli unit test.

## <a name="run-tests"></a>Esecuzione dei test

È possibile eseguire test in Visual Studio o dalla riga di comando.

### <a name="run-tests-in-visual-studio"></a>Eseguire test in Visual Studio

::: moniker range=">=vs-2019"
È possibile eseguire i test facendo clic sul collegamento **Esegui tutti** in Esplora test. In alternativa, è possibile eseguire i test selezionando uno o più test o gruppi, facendo clic con il pulsante destro del mouse e scegliendo **Esegui** dal menu di scelta rapida. I test vengono eseguiti in background ed Esplora test aggiorna e visualizza automaticamente i risultati. Inoltre, è possibile eseguire il debug dei test selezionati facendo clic con il pulsante destro del mouse e selezionando **debug**.
::: moniker-end
::: moniker range="vs-2017"
È possibile eseguire i test facendo clic sul collegamento **Esegui tutti** in Esplora test. Oppure è possibile eseguire i test selezionando uno o più test o gruppi, facendo clic con il pulsante destro del mouse e selezionando **Esegui test selezionati** dal menu di scelta rapida. I test vengono eseguiti in background ed Esplora test aggiorna e visualizza automaticamente i risultati. È inoltre possibile eseguire il debug di test selezionati scegliendo **Esegui debug test selezionati**.
::: moniker-end

Per TypeScript, gli unit test vengono eseguiti sul codice JavaScript generato.

> [!NOTE]
> Nella maggior parte degli scenari TypeScript è possibile eseguire il debug di un unit test impostando un punto di interruzione nel codice TypeScript, facendo clic con il pulsante destro del mouse su un test in Esplora test e scegliendo **debug**. Negli scenari più complessi, ad esempio in scenari in cui vengono usate le mappe di origine, è possibile che si verifichino problemi nel codice TypeScript. Come soluzione alternativa, provare a usare la `debugger` parola chiave.

> [!NOTE]
> Test di profilatura o code coverage non sono attualmente supportati.

### <a name="run-tests-from-the-command-line"></a>Eseguire test dalla riga di comando

È possibile eseguire i test dal [prompt dei comandi per gli sviluppatori](/dotnet/framework/tools/developer-command-prompt-for-vs) per Visual Studio usando il comando seguente:

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

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Aggiungere il supporto per un framework di unit test

È possibile aggiungere il supporto per altri framework di test implementando la logica di individuazione ed esecuzione tramite JavaScript. A questo scopo, aggiungere una cartella con il nome del framework di test in:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Questa cartella deve contenere un file JavaScript con lo stesso nome che esporta le due funzioni seguenti:

* `find_tests`
* `run_tests`

Per un buon esempio delle implementazioni `find_tests` e `run_tests`, vedere l'implementazione per il framework di unit test Mocha in:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

L'individuazione dei framework di test disponibili avviene all'avvio di Visual Studio. Se un framework viene aggiunto mentre Visual Studio è in esecuzione, riavviare Visual Studio per rilevare il framework. Il riavvio non è tuttavia necessario quando si apportano modifiche all'implementazione.

## <a name="unit-tests-in-other-project-types"></a>Unit test in altri tipi di progetto
È possibile scrivere unit test non solo nei progetti Node.js. Quando si aggiungono le proprietà TestFramework e TestRoot a un qualsiasi progetto C# o Visual Basic, questi test vengono enumerati e possono essere eseguiti tramite la finestra Esplora Test.

A tale scopo, fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni, scegliere **Scarica progetto**, quindi scegliere **Edit Project** (Modifica progetto). Nel file di progetto aggiungere i due elementi seguenti a un gruppo di proprietà.

> [!NOTE]
> Assicurarsi che il gruppo di proprietà al quale vengono aggiunti gli elementi non abbia una condizione specifica,
> che potrebbe causare comportamenti inaspettati.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Successivamente, aggiungere i test alla cartella radice di test specificata. A questo punto i test saranno disponibili per essere eseguiti nella finestra Esplora test. Se inizialmente non vengono visualizzati, potrebbe essere necessario ricompilare il progetto.

### <a name="unit-test-net-core-and-net-standard"></a>Unit test .NET Core e .NET Standard
Oltre alle proprietà sopra riportate, sarà necessario installare anche il pacchetto NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) e impostare la proprietà:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Alcuni framework di test possono richiedere pacchetti NPM aggiuntivi per il rilevamento dei test. Per scherzo, ad esempio, è necessario il pacchetto NPM di jest-editor-support. Se necessario, consultare la documentazione relativa al Framework specifico.
