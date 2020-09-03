---
title: Creazione di commenti in formato documentazione XML per IntelliSense per JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619539"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Creare commenti in formato documentazione XML per IntelliSense per JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I commenti relativi alla *documentazione XML* sono commenti JavaScript aggiunti a uno script per fornire informazioni sugli elementi di codice, ad esempio funzioni, campi e variabili. In Visual Studio queste descrizioni di testo vengono visualizzate con IntelliSense quando si fa riferimento alla funzione di script.

 In questo argomento viene fornita un'esercitazione di base sull'utilizzo di commenti relativi alla documentazione XML. Per informazioni sull'uso di altri elementi, ad esempio [\<var>](../ide/var-javascript.md) e [\<value>](../ide/value-javascript.md) , e per esempi di codice aggiuntivi, vedere commenti relativi alla [documentazione XML](../ide/xml-documentation-comments-javascript.md). Per informazioni su come fornire informazioni IntelliSense per un callback asincrono, ad esempio un `Promise` , vedere [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> I commenti della documentazione XML sono disponibili solo dai file, dagli assembly e dai servizi di riferimento.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Per creare commenti di documentazione XML per una funzione JavaScript

- Nella funzione aggiungere [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) gli elementi, e e precedere ogni elemento con tre barre (///).

    > [!NOTE]
    > Ogni elemento deve trovarsi su una sola riga.

     Nell'esempio seguente viene illustrata una funzione JavaScript.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Per visualizzare i commenti relativi alla documentazione XML, digitare il nome e la parentesi di apertura di una funzione contrassegnata con i commenti della documentazione XML, come nell'esempio seguente:

    ```javascript
    var areaVal = getArea(
    ```

     Quando si digita la parentesi di apertura della funzione che contiene i commenti della documentazione XML, l'editor di codice utilizza IntelliSense per visualizzare le informazioni definite nei commenti della documentazione XML.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Per creare commenti relativi alla documentazione XML per un campo JavaScript

- Nella definizione di un oggetto o di una funzione del costruttore aggiungere un [\<field>](../ide/field-javascript.md) elemento preceduto da tre barre (///).

     Nell'esempio seguente viene illustrato l'utilizzo dell' `<field>` elemento in una funzione del costruttore. Per ulteriori esempi, vedere [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Per visualizzare i commenti relativi alla documentazione XML, creare un oggetto utilizzando il costruttore di funzione contrassegnato con i commenti della documentazione XML, come nell'esempio seguente.

    ```javascript
    var eng = new Engine();
    ```

- Nella riga successiva digitare il nome dell'oggetto e un punto per visualizzare le informazioni di IntelliSense per il campo.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Per creare commenti relativi alla documentazione XML per una funzione in overload

1. Nella funzione aggiungere un [\<signature>](../ide/signature-javascript.md) elemento per ogni overload. In questi elementi aggiungere altri elementi, ad esempio `<summary>` , `<param>` e, che `<returns>` precede ogni elemento con tre barre (///).

     Nell'esempio seguente viene illustrata una funzione JavaScript di overload. In questo esempio, gli overload variano in base al tipo di parametro.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Per visualizzare i commenti relativi alla documentazione XML, digitare il nome e la parentesi di apertura della funzione contrassegnata con i commenti della documentazione XML, come nell'esempio seguente:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Per creare IntelliSense localizzato

1. Creare un file XML con commenti sulla documentazione nel formato OpenAjax MessageBundle.

    > [!IMPORTANT]
    > MessageBundle è il formato consigliato. Questo formato non è supportato in Microsoft AJAX o nei file con estensione winmd. Per informazioni sull'utilizzo del `VSDoc` formato alternativo, vedere [\<loc>](../ide/loc-javascript.md) .

     Nell'esempio seguente viene illustrato il contenuto di un file sidecar che contiene le informazioni di IntelliSense localizzate. Si tratta di un file XML che si trova in una cartella specifica delle impostazioni cultura, ad esempio JA. La cartella deve trovarsi nella stessa posizione del file con estensione js che contiene l' `<loc>` elemento. Il nome file del file XML deve corrispondere al `filename` parametro specificato nell' `<loc>` elemento.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. Nel file js aggiungere il codice seguente. L' `<loc>` elemento deve essere dichiarato prima di qualsiasi script e segue le stesse regole di utilizzo dell' `<reference>` elemento. Per ulteriori informazioni, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md) e [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. Nel file js aggiungere gli elementi della documentazione XML e le descrizioni predefinite. Impostare i `locid` valori di attributo in modo che corrispondano ai `name` valori di attributo corrispondenti dal file sidecar. Le descrizioni predefinite verranno sostituite dalle informazioni di IntelliSense localizzate, se disponibili.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Per visualizzare i commenti relativi alla documentazione XML, digitare il nome e la parentesi di apertura della funzione, come nell'esempio seguente:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Vedere anche
 [JavaScript IntelliSense](../ide/javascript-intellisense.md) [commenti sulla documentazione XML](../ide/xml-documentation-comments-javascript.md) [-pennino: procedura dettagliata: JavaScript IntelliSense in ASP.NET](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
