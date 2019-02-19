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
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54772381"
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
 Facoltativo. Il tipo di dati del parametro. Il tipo può essere uno dei seguenti:  
  
- Un linguaggio ECMAScript digitare nella specifica ECMAScript 5, ad esempio `Number` e `Object`.  
  
- Oggetto di un modello DOM, ad esempio `HTMLElement`, `Window`, e `Document`.  
  
- Funzione del costruttore JavaScript.  
  
  `integer`  
  Facoltativo. Se `type` è `Number`, specifica se il parametro è un numero intero. Impostare su `true` per indicare che il parametro è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
  `domElement`  
  Facoltativo. Questo attributo è deprecato. il `type` attributo ha la precedenza su questo attributo. Questo attributo specifica se il parametro documentato è un elemento DOM. Impostare su `true` per specificare che il parametro è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera il parametro documentato come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
  `mayBeNull`  
  Facoltativo. Specifica se il parametro documentato può essere impostato su null. Impostare su `true` per indicare che il parametro può essere impostato su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
  `elementType`  
  Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
  `elementInteger`  
  Facoltativo. Se `type` viene `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi nella matrice sono numeri interi; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
  `elementDomElement`  
  Facoltativo. Questo attributo è deprecato. il `elementType` attributo ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostato su `false`. Se il `elementType` attributo non è impostato e `elementDomElement` è impostata su `true`, IntelliSense considera ogni elemento nella matrice come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
  `elementMayBeNull`  
  Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice possono essere impostati su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
  `locid`  
  Facoltativo. L'identificatore per le informazioni di localizzazione sul parametro. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) elemento.  
  
  `parameterArray`  
  Facoltativo. Specifica se il parametro documentato può essere ripetuto nella chiamata di funzione, simile alla ripetizione di parametri supportati nel `String.format` (funzione). Impostare su `true` per indicare che il parametro può essere ripetuto; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
  `optional`  
  Facoltativo. Specifica se il parametro documentato è facoltativo nella funzione chiamante. Impostare su `true` per indicare che il parametro è facoltativo; in caso contrario, impostato su `false`.  
  
  `value`  
  Facoltativo. Specifica il codice che deve essere valutato per l'uso da IntelliSense anziché il codice della funzione. È possibile usare questo attributo è per fornire informazioni sul tipo quando il tipo di parametro non è definito. Ad esempio, è possibile usare `value=’1’` per considerare il tipo di parametro sotto forma di numero.  
  
  `description`  
  Facoltativo. Descrizione del parametro.  
  
## <a name="remarks"></a>Osservazioni  
 L'unico attributo obbligatorio è `name`. Tutti gli altri attributi sono facoltativi.  
  
 Gli elementi utilizzati per annotare le funzioni, ad esempio [ \<riepilogo >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), e [ \<restituisce >](../ide/returns-javascript.md), deve essere inserito nel corpo della funzione prima di qualsiasi istruzione.  
  
 Se sono presenti più `<param>` elementi con lo stesso nome, uno del `<param>` elementi viene usato e gli elementi ridondanti verranno ignorati. Non è definito il comportamento che determina quale elemento viene usato. Se `name` fa riferimento a un parametro inesistente, l'elemento viene ignorato.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il `<param>` elemento.  
  
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
