---
title: '&lt;param &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670366"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per un parametro in una funzione o un metodo.

## <a name="syntax"></a>Sintassi

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Parametri
 `name` Obbligatorio. Nome del parametro.

 `type` Facoltativo. Tipo di dati del parametro. Il tipo può essere uno dei seguenti:

- Tipo di linguaggio ECMAScript nella specifica ECMAScript 5, ad esempio `Number` e `Object` .

- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.

- Una funzione costruttore JavaScript.

  `integer` Facoltativo. Se `type` è `Number` , specifica se il parametro è un numero intero. Impostare su `true` per indicare che il parametro è un intero; in caso contrario, impostare su `false` . Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `domElement` Facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se il parametro documentato è un elemento DOM. Impostare su `true` per specificare che il parametro è un elemento DOM; in caso contrario, impostare su `false` . Se l' `type` attributo non è impostato e `domElement` è impostato su `true` , IntelliSense considera il parametro documentato come un oggetto `HTMLElement` quando si esegue il completamento delle istruzioni.

  `mayBeNull` Facoltativo. Specifica se il parametro documentato può essere impostato su null. Impostare su `true` per indicare che il parametro può essere impostato su null; in caso contrario, impostare su `false` . Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementType` Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.

  `elementInteger` Facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementDomElement` Facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.

  `elementMayBeNull` Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `locid` Facoltativo. Identificatore per le informazioni di localizzazione sul parametro. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nell' [\<loc>](../ide/loc-javascript.md) elemento.

  `parameterArray` Facoltativo. Specifica se il parametro documentato può essere ripetuto nella chiamata di funzione, in modo analogo ai parametri ripetuti supportati nella `String.format` funzione. Impostare su `true` per indicare che il parametro può essere ripetuto; in caso contrario, impostare su `false` . Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `optional` Facoltativo. Specifica se il parametro documentato è facoltativo nella funzione chiamante. Impostare su `true` per indicare che il parametro è facoltativo. in caso contrario, impostare su `false` .

  `value` Facoltativo. Specifica il codice che deve essere valutato per l'uso da parte di IntelliSense anziché dal codice della funzione stessa. È possibile utilizzare questo attributo per fornire informazioni sul tipo quando il tipo di parametro non è definito. Ad esempio, è possibile usare `value=’1’` per trattare il tipo di parametro come numero.

  `description` Facoltativo. Descrizione del parametro.

## <a name="remarks"></a>Osservazioni
 L'unico attributo obbligatorio è `name` . Tutti gli altri attributi sono facoltativi.

 Gli elementi utilizzati per annotare le funzioni, ad esempio [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) e [\<returns>](../ide/returns-javascript.md) , devono essere inseriti nel corpo della funzione prima di qualsiasi istruzione.

 Se sono presenti più `<param>` elementi con lo stesso nome, viene utilizzato uno degli `<param>` elementi e gli elementi ridondanti vengono ignorati. Il comportamento che determina quale elemento viene utilizzato non è definito. Se `name` fa riferimento a un parametro non esistente, l'elemento viene ignorato.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<param>`.

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

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
