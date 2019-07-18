---
title: '&lt;Restituisce&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81a9a42a104adb2a9d9a9aba483e2588d7332868
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203531"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per il risultato di una chiamata di funzione o un metodo.  
  
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
 `type`  
 facoltativo. Il tipo di dati del valore restituito. Il tipo può essere uno dei seguenti:  
  
- Un linguaggio ECMAScript digitare nella specifica ECMAScript 5, ad esempio `Number` e `Object`.  
  
- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.  
  
- Una funzione costruttore JavaScript.  
  
  `integer`  
  facoltativo. Se `type` è `Number`, specifica se il valore restituito è un numero intero. Impostare su `true` per indicare che il valore restituito è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `domElement`  
  facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se il valore restituito documentato è un elemento DOM. Impostare su `true` per specificare che il valore restituito è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera il valore restituito documentato come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
  `mayBeNull`  
  facoltativo. Specifica se il documento restituito può essere impostato su null. Impostare su `true` per indicare che il valore restituito può essere impostato su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `elementType`  
  facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
  `elementInteger`  
  facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `elementDomElement`  
  facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.  
  
  `elementMayBeNull`  
  facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `locid`  
  facoltativo. L'identificatore per le informazioni di localizzazione sul valore restituito. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nel tag [\<loc>](../ide/loc-javascript.md).  
  
  `value`  
  facoltativo. Specifica il codice che deve essere valutato per l'uso da IntelliSense anziché il codice della funzione. Ad esempio, è possibile usare questo attributo per fornire IntelliSense per i callback asincroni, ad esempio un `Promise`. Usando il `value` dell'attributo con il `<returns>` elemento può migliorare le prestazioni di IntelliSense ignorando l'esecuzione di codice particolarmente lunghi.  
  
  `description`  
  facoltativo. Descrizione del valore restituito.  
  
## <a name="remarks"></a>Osservazioni  
 Il `<returns>` elemento deve essere inserito nel corpo della funzione prima di qualsiasi istruzione.  
  
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
