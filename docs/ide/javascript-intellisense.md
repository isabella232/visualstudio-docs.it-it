---
title: IntelliSense per JavaScript
description: Informazioni su come Visual Studio intelliSense più ricco, il supporto per le moderne funzionalità JavaScript e le funzionalità di produttività migliorate.
ms.custom: SEO-VS-2020
ms.date: 06/28/2017
ms.topic: conceptual
ms.technology: vs-javascript
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c5f997b7a4be43e6a8482a6282ecaaf2e3babf3e13bb5b08e734bb149b9ea75
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357830"
---
# <a name="javascript-intellisense"></a>IntelliSense per JavaScript

Visual Studio include potenti strumenti di modifica per JavaScript pronti all'uso. Visual Studio, gestito da un servizio di linguaggio basato su TypeScript, offre una modalità IntelliSense più completa, il supporto di funzionalità JavaScript aggiornate e funzioni di produttività migliorate quali Vai a definizione, il refactoring e altro ancora.

> [!NOTE]
> A partire da Visual Studio 2017, JavaScript Language Service usa un nuovo motore per il servizio di linguaggio (denominato "Salsa"). Per i dettagli proseguire la lettura di questo articolo. È anche possibile leggere [questo post di blog](https://devblogs.microsoft.com/visualstudio/previewing-salsa-javascript-language-service-visual-studio-15/). Le nuove funzioni di modifica si applicano principalmente anche a Visual Studio Code. Per altre informazioni vedere la [documentazione di Visual Studio Code](https://code.visualstudio.com/docs/languages/javascript).

Per altre informazioni sulla funzionalità IntelliSense generale di Visual Studio, vedere [Uso di IntelliSense](../ide/using-intellisense.md).

## <a name="whats-new-in-the-javascript-language-service-in-visual-studio-2017"></a>Novità di JavaScript Language Service in Visual Studio 2017

A partire da Visual Studio 2017, JavaScript IntelliSense visualizza una quantità molto più elevata di informazioni su elenchi di parametri e membri. Le nuove informazioni sono specificate dal servizio di linguaggio TypeScript, che usa l'analisi statica in background per un'interpretazione più approfondita del codice.

Per ottenere le informazioni necessarie, TypeScript usa diverse fonti:

- [IntelliSense basato sull'inferenza del tipo](#TypeInference)
- [IntelliSense basato su JSDoc](#JsDoc)
- [IntelliSense basato su file di dichiarazione TypeScript](#TsDeclFiles)
- [Acquisizione automatica delle definizioni dei tipi](#Auto)

<a name="TypeInference"></a>

### <a name="intellisense-based-on-type-inference"></a>IntelliSense basato sull'inferenza del tipo

In JavaScript nella maggior parte dei casi non sono disponibili informazioni esplicite relative ai tipi. In genere è abbastanza semplice intuire un tipo in base al contesto del codice circostante.
Questo processo è detto inferenza del tipo.

Per una variabile o una proprietà, il tipo è in genere il tipo del valore usato per l'inizializzazione oppure l'assegnazione di un valore più recente.

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

Per una funzione, il tipo restituito può essere dedotto dalle istruzioni return.

Per i parametri di funzione l'inferenza non è attualmente disponibile, ma è possibile risolvere il problema mediante i file *.d.ts* JSDoc o TypeScript (vedere le sezioni successive).

È anche disponibile una funzionalità di inferenza speciale per i seguenti elementi:

- Classi "in stile ES3", specificate mediante una funzione costruttore e assegnazioni alla proprietà prototype.
- Modelli di modulo in stile CommonJS, specificati come assegnazioni di proprietà nell'oggetto `exports` oppure assegnazioni alla proprietà `module.exports`.

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

<a name="JsDoc"></a>

### <a name="intellisense-based-on-jsdoc"></a>IntelliSense basato su JSDoc

Quando l'inferenza del tipo non specifica le informazioni sul tipo desiderate (o si vuole aggiungere supporto alla documentazione), è possibile includere informazioni sul tipo in modo esplicito tramite le annotazioni JSDoc.  Ad esempio, per assegnare un tipo specifico a un oggetto parzialmente dichiarato si può usare il tag `@type` come illustrato di seguito:

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

Come detto, l'inferenza non è mai valida per i parametri funzione. Tuttavia con il tag JSDoc `@param` è possibile aggiungere tipi anche ai parametri funzione.

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```

Vedere [supporto per JSDoc in JavaScript](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript) per le annotazioni di JsDoc attualmente supportate.

<a name="TsDeclFiles"></a>
### <a name="intellisense-based-on-typescript-declaration-files"></a>IntelliSense basato su file dichiarazione TypeScript

Dato che ora JavaScript e TypeScript si basano sullo stesso servizio di linguaggio, sono in grado di interagire in modo più completo. Ad esempio è possibile aggiungere codice IntelliSense JavaScript per i valori dichiarati in un file *.d.ts* (vedere [documentazione TypeScript](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html)), mentre i tipi quali interfacce e classi dichiarate in TypeScript sono disponibili per l'uso come tipi nei commenti JsDoc.

Di seguito viene visualizzato un esempio semplice di file di definizione TypeScript che specifica questo tipo di informazioni (attraverso un'interfaccia) a un file JavaScript nello stesso progetto (mediante un tag `JsDoc`).

![File di definizione TypeScript](https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png)

<a name="Auto"></a>
### <a name="automatic-acquisition-of-type-definitions"></a>Acquisizione automatica delle definizioni dei tipi

Nell'ambito TypeScript, le API delle librerie JavaScript più diffuse sono descritte da file *.d.ts* e il repository più comune per tali definizioni si trova in [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Per impostazione predefinita il servizio di linguaggio Salsa prova a rilevare le librerie JavaScript in uso, quindi scarica e crea automaticamente un riferimento al file *.d.ts* corrispondente che descrive la libreria, al fine di fornire un'esecuzione IntelliSense più completa. I file vengono scaricati in una cache posta all'interno della cartella dell'utente in *%LOCALAPPDATA%\Microsoft\TypeScript*.

> [!NOTE]
> Questa funzionalità è **disabilitata** per impostazione predefinita se si usa un file di configurazione *tsconfig.json*, ma può essere impostata come abilitata con le modalità descritte di seguito.

Attualmente il rilevamento automatico funziona per le dipendenze scaricate da npm (mediante la lettura del file *package.json*), Bower (mediante la lettura del file *bower.json*) e per singoli file del progetto corrispondenti a un elenco contenente circa 400 tra le librerie JavaScript più diffuse. Se ad esempio nel progetto è presente *jquery-1.10.min.js*, verrà recuperato e caricato il file *jquery.d.ts* per garantire una funzionalità di modifica più completa. Tale file *.d.ts* non avrà alcun impatto sul progetto.

Se non si vuole usare l'acquisizione automatica, disattivarla mediante l'aggiunta di un file di configurazione, come descritto di seguito. È comunque possibile inserire manualmente file di definizione da usare direttamente nel progetto.

## <a name="see-also"></a>Vedi anche

- [Uso di IntelliSense](../ide/using-intellisense.md)
- [JavaScript support (Supporto per JavaScript) (Visual Studio per Mac)](/visualstudio/mac/javascript)
