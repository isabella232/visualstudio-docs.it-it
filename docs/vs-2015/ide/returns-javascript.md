---
title: '&lt;Restituisce&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dfe2c3d8e9c91927f7f4d0848b8d180132646614
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526403"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Restituisce&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
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
 Facoltativo. Il tipo di dati del valore restituito. Il tipo può essere uno dei seguenti:  
  
-   Un linguaggio ECMAScript digitare nella specifica ECMAScript 5, ad esempio `Number` e `Object`.  
  
-   Oggetto di un modello DOM, ad esempio `HTMLElement`, `Window`, e `Document`.  
  
-   Funzione del costruttore JavaScript.  
  
 `integer`  
 Facoltativo. Se `type` è `Number`, specifica se il valore restituito è un numero intero. Impostare su `true` per indicare che il valore restituito è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Facoltativo. Questo attributo è deprecato. il `type` attributo ha la precedenza su questo attributo. Questo attributo specifica se il valore restituito documentato è un elemento DOM. Impostare su `true` per specificare che il valore restituito è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera il valore restituito documentato come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
 `mayBeNull`  
 Facoltativo. Specifica se il documento restituito può essere impostato su null. Impostare su `true` per indicare che il valore restituito può essere impostato su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
 `elementInteger`  
 Facoltativo. Se `type` viene `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi nella matrice sono numeri interi; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Facoltativo. Questo attributo è deprecato. il `elementType` attributo ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostato su `false`. Se il `elementType` attributo non è impostato e `elementDomElement` è impostata su `true`, IntelliSense considera ogni elemento nella matrice come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice possono essere impostati su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `locid`  
 Facoltativo. L'identificatore per le informazioni di localizzazione sul valore restituito. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) tag.  
  
 `value`  
 Facoltativo. Specifica il codice che deve essere valutato per l'uso da IntelliSense anziché il codice della funzione. Ad esempio, è possibile usare questo attributo per fornire IntelliSense per i callback asincroni, ad esempio un `Promise`. Usando il `value` dell'attributo con il `<returns>` elemento può migliorare le prestazioni di IntelliSense ignorando l'esecuzione di codice particolarmente lunghi.  
  
 `description`  
 Facoltativo. Descrizione del valore restituito.  
  
## <a name="remarks"></a>Note  
 Il `<returns>` elemento deve essere inserito nel corpo della funzione prima di qualsiasi istruzione.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il `<returns>` elemento.  
  
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



