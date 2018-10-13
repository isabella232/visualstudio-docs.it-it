---
title: '&lt;valore&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ad9f3834efd56ffbddb4686e741b7d85d3363c1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264173"
---
# <a name="ltvaluegt-javascript"></a>&lt;valore&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per `get` e `set` funzioni per ECMAScript 3 proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<value type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID">description  
</value>  
```  
  
#### <a name="parameters"></a>Parametri  
 `type`  
 Facoltativo. Il tipo di dati della proprietà. Il tipo può essere uno dei seguenti:  
  
-   Un tipo di linguaggio ECMAScript che è la specifica ECMAScript 5, quali `Number` e `Object`.  
  
-   Oggetto di un modello DOM, ad esempio `HTMLElement`, `Window`, e `Document`.  
  
-   Funzione del costruttore JavaScript.  
  
 `integer`  
 Facoltativo. Se `type` è `Number`, specifica se la proprietà è un numero intero. Impostare su `true` per indicare che la proprietà è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `domElement`  
 Facoltativo. Questo attributo è deprecato. il `type` attributo ha la precedenza su questo attributo. Questo attributo specifica se la proprietà documentata è un elemento DOM. Impostare su `true` per specificare che la proprietà è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera la proprietà documentata come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
 `mayBeNull`  
 Facoltativo. Specifica se la proprietà documentata può essere impostata su null. Impostare su `true` per indicare che la proprietà può essere impostata su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementType`  
 Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
 `elementInteger`  
 Facoltativo. Se `type` viene `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi nella matrice sono numeri interi; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `elementDomElement`  
 Facoltativo. Questo attributo è deprecato. il `elementType` attributo ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in caso contrario, impostato su `false`. Se il `elementType` attributo non è impostato e `elementDomElement` è impostata su `true`, IntelliSense considera ogni elemento nella matrice come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
 `elementMayBeNull`  
 Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice possono essere impostati su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
 `locid`  
 Facoltativo. L'identificatore per le informazioni di localizzazione sulla proprietà. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `description`  
 Facoltativo. Descrizione della proprietà.  
  
## <a name="remarks"></a>Note  
 Usare le proprietà di ECMAScript 5 il [ \<riepilogo >](../ide/summary-javascript.md) elemento.  
  
 Usare la `<value>` elemento immediatamente prima di `get` o `set` (funzione).  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il `<value>` elemento in un `get` (funzione).  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)



