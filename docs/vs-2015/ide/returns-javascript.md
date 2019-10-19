---
title: '&lt;returns &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669959"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per il risultato di una chiamata di funzione o di metodo.

## <a name="syntax"></a>Sintassi

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parametri
 `type` Facoltativo. Tipo di dati del valore restituito. Il tipo può essere uno dei seguenti:

- Tipo di linguaggio ECMAScript nella specifica ECMAScript 5, ad esempio `Number` e `Object`.

- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.

- Una funzione costruttore JavaScript.

  `integer` Facoltativo. Se `type` è `Number`, specifica se il valore restituito è un numero intero. Impostare su `true` per indicare che il valore restituito è un numero intero. in caso contrario, impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `domElement` Facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se il valore restituito documentato è un elemento DOM. Impostare su `true` per specificare che il valore restituito è un elemento DOM; in caso contrario, impostare su `false`. Se l'attributo `type` non è impostato e `domElement` è impostato su `true`, IntelliSense considera il valore restituito documentato come `HTMLElement` durante l'esecuzione del completamento delle istruzioni.

  `mayBeNull` Facoltativo. Specifica se il valore restituito documentato può essere impostato su null. Impostare su `true` per indicare che il valore restituito può essere impostato su null. in caso contrario, impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementType` Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.

  `elementInteger` Facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementDomElement` Facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.

  `elementMayBeNull` Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `locid` Facoltativo. Identificatore per le informazioni di localizzazione sul valore restituito. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nel tag [\<loc>](../ide/loc-javascript.md).

  `value` Facoltativo. Specifica il codice che deve essere valutato per l'uso da parte di IntelliSense anziché dal codice della funzione stessa. Ad esempio, è possibile usare questo attributo per fornire IntelliSense per callback asincroni, ad esempio un `Promise`. L'utilizzo dell'attributo `value` con l'elemento `<returns>` può migliorare le prestazioni di IntelliSense ignorando la lunga esecuzione del codice.

  `description` Facoltativo. Descrizione del valore restituito.

## <a name="remarks"></a>Osservazioni
 L'elemento `<returns>` deve essere inserito nel corpo della funzione prima di qualsiasi istruzione.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<returns>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
