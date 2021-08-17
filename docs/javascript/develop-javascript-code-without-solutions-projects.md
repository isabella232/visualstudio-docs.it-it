---
title: Scrivere codice JavaScript in Visual Studio senza una soluzione o un progetto
titleSuffix: ''
description: Visual Studio offre supporto per la creazione di codice senza una dipendenza da un file di progetto o di soluzione
ms.custom: seodec18
ms.date: 09/24/2018
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
ms.openlocfilehash: c1cad687f73af5eb59f23a2d176e5b8facd3da40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028020"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Sviluppare il codice JavaScript e TypeScript in Visual Studio senza soluzioni o progetti

A partire da Visual Studio 2017 è possibile [sviluppare codice senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), quindi aprire una cartella del codice e iniziare immediatamente a lavorare con le opzioni di supporto di un editor avanzato, ad esempio IntelliSense, la ricerca, il refactoring, il debug e altro ancora. Oltre a queste funzionalità, Node.js Tools for Visual Studio aggiunge il supporto per la compilazione dei file TypeScript, la gestione dei pacchetti npm e l'esecuzione degli script npm.

Per iniziare, selezionare **Apri cartella**  >  **file**  >  **sulla** barra degli strumenti. Esplora soluzioni visualizza tutti i file della cartella ed è possibile aprire qualsiasi file per iniziare ad apportare modifiche. Visual Studio indicizza in background i file per abilitare le funzionalità di npm, compilazione e debug.

> [!IMPORTANT]
> Molte delle funzionalità descritte in questo articolo, inclusa l'integrazione di npm, richiedono Visual Studio 2017 versione 15.8 o successive. È Visual Studio **Node.js carico di lavoro Sviluppo** di applicazioni.

## <a name="npm-integration"></a>Integrazione di npm

Se la cartella aperta contiene un file *package.json*, è possibile fare clic con il pulsante destro del mouse su *package.json* per visualizzare un menu di scelta rapida specifico per npm.

![Menu npm in Esplora soluzioni](../javascript/media/solution-explorer-npm-ctx.png)

Nel menu di scelta rapida è possibile gestire i pacchetti installati da npm nello stesso modo in cui si [gestiscono i pacchetti npm](npm-package-management.md) quando si usa un file di progetto.

Inoltre, il menu consente anche di eseguire gli script definiti nell'elemento `scripts` in *package.json*. Questi script usano la versione di Node.js disponibile nella variabile di ambiente `PATH`. Gli script vengono eseguiti in una nuova finestra. Questo è un ottimo modo di eseguire build o script.

## <a name="build-and-debug"></a>Compilazione e debug

### <a name="packagejson"></a>package.json
Se il file *package.json* nella cartella specifica un elemento `main`, il comando **Debug** sarà disponibile nel menu di scelta rapida per *package.json*.
Facendo clic sul comando si avvia *node.exe* con lo script specificato come argomento.

### <a name="javascript-files"></a>File JavaScript
Per eseguire il debug dei file JavaScript, fare clic con il pulsante destro del mouse su un file e selezionare **Debug** dal menu di scelta rapida. In questo modo viene avviato *node.exe* con quel file JavaScript come argomento.

### <a name="typescript-files-and-tsconfigjson"></a>File TypeScript e tsconfig.json
Se la cartella non contiene un file *tsconfig.json*, è possibile fare clic con il pulsante destro del mouse su un file TypeScript per visualizzare i comandi del menu di scelta rapida per compilare ed eseguire il debug di tale file. Quando si usano questi comandi si compila o si esegue il debug usando *tsc.exe* con le opzioni predefinite. È necessario compilare il file prima di eseguire il debug.

> [!NOTE]
> Quando si compila codice TypeScript, si usa la versione più recente installata in `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

Se la cartella contiene un file *tsconfig.json*, è possibile fare clic con il pulsante destro del mouse su un file TypeScript per visualizzare un comando di menu per eseguire il debug di tale file. L'opzione viene visualizzata solo se non è specificato alcun `outFile` in *tsconfig.json*. Se è specificato un `outFile`, è possibile eseguire il debug di tale file facendo clic con il pulsante destro del mouse su *tsconfig.json* e selezionando l'opzione corretta. Il file `tsconfig.json` offre inoltre un'opzione di compilazione che consente di specificare le opzioni del compilatore.

> [!NOTE]
> È possibile trovare altre informazioni su *tsconfig.json* nella [pagina del manuale di TypeScript relativa a tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Unit test
È possibile abilitare l'integrazione degli unit test in Visual Studio specificando una radice di test nel file *package.json*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Il test runner consente di enumerare i pacchetti installati in locale per determinare i framework di test da usare.
Se non viene riconosciuto nessun framework supportato, il test runner usa *ExportRunner* per impostazione predefinita. Gli altri framework supportati sono i seguenti:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

Dopo aver aperto Esplora test (scegliere  >  **Test Windows**  >  **Esplora test),** Visual Studio individua e visualizza i test.

> [!NOTE]
> Se l'applicazione è scritta in TypeScript, il test runner enumererà solo i file JavaScript che sono da compilare per primi.
