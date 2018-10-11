---
title: '&lt;var&gt; (JavaScript) | Microsoft Docs'
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
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d66c6a001d077fc68e99e479ac3352c8113f0c4e
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880396"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](/visualstudio/).  
  
Specifica le informazioni sulla documentazione per una variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<var type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID">description  
</var>   
```  
  
#### <a name="parameters"></a>Parametri  
 `type`  
 Facoltativo. Il tipo di dati della variabile. Il tipo può essere uno dei seguenti:  
  
-   Un tipo di linguaggio ECMAScript che è la specifica ECMAScript 5, quali `Number` e `Object`.  
  
-   Oggetto di un modello DOM, ad esempio `HTMLElement`, `Window`, e `Document`.  
  
-   Funzione del costruttore JavaScript.  
  
 `integer`  
 Facoltativo. Se `type` è `Number`, specifica se la variabile è un numero intero. Impostare su `true` per indicare che la variabile è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Facoltativo. Questo attributo è deprecato. il `type` attributo ha la precedenza su questo attributo. Questo attributo specifica se la variabile documentata è un elemento DOM. Impostare su `true` per specificare che la variabile è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera la variabile documentata come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
 `mayBeNull`  
 Facoltativo. Specifica se la variabile documentata può essere impostata su null. Impostare su `true` per indicare che la variabile può essere impostata su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
 `elementInteger`  
 Facoltativo. Se `type` viene `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi nella matrice sono numeri interi; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Facoltativo. Questo attributo è deprecato. il `elementType` attributo ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostato su `false`. Se il `elementType` attributo non è impostato e `elementDomElement` è impostata su `true`, IntelliSense considera ogni elemento nella matrice come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice possono essere impostati su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `helpKeyword`  
 Facoltativo. La parola chiave per la Guida F1.  
  
 `locid`  
 Facoltativo. L'identificatore per le informazioni di localizzazione sulla variabile. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) tag.  
  
 `description`  
 Facoltativo. Descrizione della variabile.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il `<var>` elemento.  
  
```javascript  
/// <var>A rectangle that has a width of 5.</var>  
var Rectangle = {  
    /// <field type = 'Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type = 'Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)



