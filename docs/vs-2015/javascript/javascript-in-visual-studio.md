---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b9005b6cf7f23639481505a4727f8faa08241684
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433476"
---
# <a name="javascript-in-visual-studio"></a>JavaScript in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript è un ottimo linguaggio di Visual Studio. È possibile usare la maggior parte o tutti gli strumenti di modifica standard (frammenti di codice, IntelliSense e così via) quando si scrive codice JavaScript nell'IDE di Visual Studio. È possibile scrivere codice JavaScript per molti tipi di applicazioni e servizi.

 Per la documentazione di riferimento del linguaggio JavaScript, vedere [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 È possibile che vengano richieste versioni specifiche di Visual Studio o estensioni specifiche di Visual Studio per sviluppare determinati tipi di applicazioni e servizi con HTML e JavaScript. L'elenco seguente include i collegamenti ad altre informazioni.

- Per creare app multipiattaforma con Apache Cordova, [scaricare Strumenti di Visual Studio per Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Per creare app di [Windows Store](http://dev.windows.com/develop), [Windows Phone](http://dev.windows.com/develop) e app universali, che supportano entrambe le piattaforme, [scaricare gli strumenti](https://developer.microsoft.com/windows/downloads).

- Per creare servizi basati sul cloud, visitare il [sito Web di Microsoft Azure](http://azure.microsoft.com/documentation/).

- Per creare siti Web e app Web, [visitare il sito ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  > È possibile creare un sito Web ASP.NET vuoto e usarlo per la programmazione HTML, CSS e JavaScript. Il file Webconfig fornito da ASP.NET consente il debug in Visual Studio (o è possibile usare gli strumenti F12 quando si esegue l'app).

  L'editor JavaScript in Visual Studio fornisce il supporto IntelliSense. Per altre informazioni, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Novità in JavaScript
 Nuove funzionalità per JavaScript sono elencate nella tabella seguente.

|Funzionalità|Descrizione|
|-------------|-----------------|
|Classi|La nuova sintassi supporta la dichiarazione delle [classi](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Suggerimenti|I [suggerimenti](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) consentono una codifica asincrona più semplice e chiara. I costruttori di suggerimenti sono supportati, con i metodi di utilità `all` e `race`.|
|Iterators|Ora è possibile scorrere gli oggetti iterabili (tra cui matrici, oggetti di tipo matrice e iteratori), richiamando un hook di iterazione personalizzato con istruzioni da eseguire per il valore di ogni singola proprietà. Per altre informazioni, vedere [Iteratori e Generatori](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Nota:**  I generatori non sono ancora supportati.|
|Funzioni freccia|La funzione freccia (=>) fornisce una sintassi abbreviata per la parola chiave `function` che offre un'associazione `this` lessicale.|
|Nuovi metodi per gli oggetti predefiniti|Gli oggetti predefiniti [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Math](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object) e [String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) includono diverse nuove proprietà e funzioni di utilità per la modifica e il controllo dei dati.|
|Miglioramenti dei valori letterali di oggetto|Gli oggetti ora supportano proprietà calcolate, definizioni di metodo concise e sintassi abbreviata per le proprietà il cui valore viene inizializzato su una variabile con lo stesso nome. Per altre informazioni, vedere [Creazione di oggetti](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxy|I [proxy](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) abilitano il comportamento personalizzato per gli oggetti.|
|Parametri rest|I parametri rest consentono di convertire in una matrice gli argomenti consecutivi in una chiamata di funzione. Per altre informazioni, vedere [Funzioni](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operatore spread|L'[operatore spread](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) (`…`) espande le espressioni iterabili in singoli argomenti. Ad esempio, `a.b(…array)` è quasi come `a.b.apply(a, array)`.|
|Simboli|Gli oggetti [Symbol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) consentono di aggiungere proprietà agli oggetti esistenti senza possibilità di interferenza con le proprietà di questi ultimi, senza alcuna visibilità imprevista e senza altre aggiunte non coordinate mediante altro codice.|
|Stringhe modello|Le [stringhe modello](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) sono valori letterali stringa che consentono di valutare le espressioni e di concatenarle con il valore letterale stringa.|
|Miglioramenti di Unicode|Sono stati apportati miglioramenti al supporto per Unicode. Ad esempio, un nuovo formato di sequenza di escape supporta i punti di codice "astrali" (punti di codice con più di quattro cifre esadecimali). Per altre informazioni, vedere [Caratteri speciali](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|Un [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) è una raccolta di oggetti che vengono sottoposti a Garbage Collection se non vi si fa riferimento in nessun altro punto.|
