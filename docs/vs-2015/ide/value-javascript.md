---
title: '&lt;valore&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179318"
---
# <a name="ltvaluegt-javascript"></a>&lt;value&gt; (JavaScript)
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
 facoltativo. Il tipo di dati della proprietà. Il tipo può essere uno dei seguenti:  
  
- Un tipo di linguaggio ECMAScript incluso nella specifica ECMAScript 5, ad esempio `Number` e `Object`.  
  
- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.  
  
- Una funzione costruttore JavaScript.  
  
  `integer`  
  facoltativo. Se `type` è `Number`, specifica se la proprietà è un numero intero. Impostare su `true` per indicare che la proprietà è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `domElement`  
  facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se la proprietà documentata è un elemento DOM. Impostare su `true` per specificare che la proprietà è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera la proprietà documentata come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
  `mayBeNull`  
  facoltativo. Specifica se la proprietà documentata può essere impostata su null. Impostare su `true` per indicare che la proprietà può essere impostata su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `elementType`  
  facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.  
  
  `elementInteger`  
  facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `elementDomElement`  
  facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.  
  
  `elementMayBeNull`  
  facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.  
  
  `locid`  
  facoltativo. L'identificatore per le informazioni di localizzazione sulla proprietà. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nell'elemento [\<loc>](../ide/loc-javascript.md).  
  
  `description`  
  facoltativo. Descrizione della proprietà.  
  
## <a name="remarks"></a>Osservazioni  
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
