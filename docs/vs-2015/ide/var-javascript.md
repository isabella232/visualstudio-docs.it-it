---
title: '&lt;var&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663066"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica informazioni di documentazione per una variabile.

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
 `type` Facoltativo. Tipo di dati della variabile. Il tipo può essere uno dei seguenti:

- Un tipo di linguaggio ECMAScript incluso nella specifica ECMAScript 5, ad esempio `Number` e `Object`.

- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.

- Una funzione costruttore JavaScript.

  `integer` Facoltativo. Se `type` è `Number`, specifica se la variabile è un numero intero. Impostare su `true` per indicare che la variabile è un numero intero; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `domElement` Facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se la variabile documentata è un elemento DOM. Impostare su `true` per specificare che la variabile è un elemento DOM; in alternativa impostare su `false`. Se l'attributo `type` non è impostato e `domElement` è `true`, IntelliSense considera la variabile documentata come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.

  `mayBeNull` Facoltativo. Specifica se la variabile documentata può essere impostata su null. Impostare su `true` per indicare che la variabile può essere impostata su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementType` Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.

  `elementInteger` Facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementDomElement` Facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.

  `elementMayBeNull` Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `helpKeyword` Facoltativo. Parola chiave per Guida F1.

  `locid` Facoltativo. Identificatore per le informazioni di localizzazione sulla variabile. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nel tag [\<loc>](../ide/loc-javascript.md).

  `description` Facoltativo. Descrizione della variabile.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<var>`.

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
