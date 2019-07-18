---
title: '&lt;param&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a8477de8bf84950d778d4ce843522be35b2d7387
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203752"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per un parametro in una funzione o metodo.  
  
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
 `name`  
 Obbligatorio. Nome del parametro.  
  
 `type`  
 facoltativo. Il tipo di dati del parametro. Il tipo può essere uno dei seguenti:  
  
- Un linguaggio ECMAScript digitare nella specifica ECMAScript 5, ad esempio `Number` e `Object`.  
  
- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.  
  
- Una funzione costruttore JavaScript.  
  
  `integer`  
  facoltativo. Se `type` è `Number`, specifica se il parametro è un numero intero. Impostare su `true` per indicare che il parametro è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `domElement`  
  facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se il parametro documentato è un elemento DOM. Impostare su `true` per specificare che il parametro è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera il parametro documentato come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
  `mayBeNull`  
  facoltativo. Specifica se il parametro documentato può essere impostato su null. Impostare su `true` per indicare che il parametro può essere impostato su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `elementType`  
  facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
  `elementInteger`  
  facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `elementDomElement`  
  facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.  
  
  `elementMayBeNull`  
  facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `locid`  
  facoltativo. L'identificatore per le informazioni di localizzazione sul parametro. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nell'elemento [\<loc>](../ide/loc-javascript.md).  
  
  `parameterArray`  
  facoltativo. Specifica se il parametro documentato può essere ripetuto nella chiamata di funzione, simile alla ripetizione di parametri supportati nel `String.format` (funzione). Impostare su `true` per indicare che il parametro può essere ripetuto; in caso contrario, impostato su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `optional`  
  facoltativo. Specifica se il parametro documentato è facoltativo nella funzione chiamante. Impostare su `true` per indicare che il parametro è facoltativo; in caso contrario, impostato su `false`.  
  
  `value`  
  facoltativo. Specifica il codice che deve essere valutato per l'uso da IntelliSense anziché il codice della funzione. È possibile usare questo attributo è per fornire informazioni sul tipo quando il tipo di parametro non è definito. Ad esempio, è possibile usare `value=’1’` per considerare il tipo di parametro sotto forma di numero.  
  
  `description`  
  facoltativo. Descrizione del parametro.  
  
## <a name="remarks"></a>Osservazioni  
 L'unico attributo obbligatorio è `name`. Tutti gli altri attributi sono facoltativi.  
  
 Gli elementi utilizzati per annotare le funzioni, ad esempio [ \<riepilogo >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), e [ \<restituisce >](../ide/returns-javascript.md), deve essere inserito nel corpo della funzione prima di qualsiasi istruzione.  
  
 Se sono presenti più `<param>` elementi con lo stesso nome, uno del `<param>` elementi viene usato e gli elementi ridondanti verranno ignorati. Non è definito il comportamento che determina quale elemento viene usato. Se `name` fa riferimento a un parametro inesistente, l'elemento viene ignorato.  
  
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
