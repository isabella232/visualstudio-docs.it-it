---
title: '&lt;valore &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656390"
---
# <a name="ltvaluegt-javascript"></a>&lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione per le `get` `set` funzioni e per le proprietà ECMAScript 3.

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
 `type` Facoltativo. Tipo di dati della proprietà. Il tipo può essere uno dei seguenti:

- Un tipo di linguaggio ECMAScript incluso nella specifica ECMAScript 5, ad esempio `Number` e `Object`.

- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.

- Una funzione costruttore JavaScript.

  `integer` Facoltativo. Se `type` è `Number` , specifica se la proprietà è un numero intero. Impostare su `true` per indicare che la proprietà è un intero; in caso contrario, impostare su `false` . Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `domElement` Facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se la proprietà documentata è un elemento DOM. Impostare su `true` per specificare che la proprietà è un elemento DOM; in caso contrario, impostare su `false` . Se l' `type` attributo non è impostato e `domElement` è impostato su `true` , IntelliSense considera la proprietà documentata come un oggetto `HTMLElement` durante l'esecuzione del completamento delle istruzioni.

  `mayBeNull` Facoltativo. Specifica se la proprietà documentata può essere impostata su null. Impostare su `true` per indicare che la proprietà può essere impostata su null; in caso contrario, impostare su `false` . Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementType` Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.

  `elementInteger` Facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementDomElement` Facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.

  `elementMayBeNull` Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `locid` Facoltativo. Identificatore per le informazioni di localizzazione sulla proprietà. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nell' [\<loc>](../ide/loc-javascript.md) elemento.

  `description` Facoltativo. Descrizione della proprietà.

## <a name="remarks"></a>Osservazioni
 Le proprietà ECMAScript 5 usano l' [\<summary>](../ide/summary-javascript.md) elemento.

 Usare l' `<value>` elemento immediatamente prima della `get` `set` funzione o.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l' `<value>` elemento su una `get` funzione.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
