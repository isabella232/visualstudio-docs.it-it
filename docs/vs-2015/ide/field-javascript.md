---
title: '&lt;field &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663863"
---
# <a name="ltfieldgt-javascript"></a>&lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica le informazioni sulla documentazione, inclusa una descrizione, per un campo o un membro definito in un oggetto.

## <a name="syntax"></a>Sintassi

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>Parametri
 `name` il nome del campo o del membro. Quando l'elemento `<field>` viene usato in una funzione del costruttore, `name` è obbligatorio e definisce il membro a cui viene applicato il tag. Quando l'elemento `<field>` annota direttamente un campo, questo attributo viene ignorato e il nome usato da Visual Studio è il nome del campo effettivo nel codice sorgente.

 `static` Facoltativo. Specifica se il campo è un membro della funzione del costruttore o un membro dell'oggetto restituito dalla funzione del costruttore. Impostare su `true` per trattare il campo come membro della funzione del costruttore. Impostare su `false` per trattare il campo come membro dell'oggetto restituito dalla funzione del costruttore.

 `type` Facoltativo. Tipo di dati del campo. Il tipo può essere uno dei seguenti:

- Tipo di linguaggio ECMAScript nella specifica ECMAScript 5, ad esempio `Number` e `Object`.

- Un oggetto DOM, ad esempio `HTMLElement`, `Window` e `Document`.

- Una funzione costruttore JavaScript.

  `integer` Facoltativo. Se `type` è `Number`, specifica se il campo è un numero intero. Impostare su `true` per indicare che il campo è un numero intero. in caso contrario, impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `domElement` Facoltativo. Questo attributo è deprecato. L'attributo `type` ha la precedenza su questo attributo. Questo attributo specifica se il campo documentato è un elemento DOM. Impostare su `true` per specificare che il campo è un elemento DOM; in caso contrario, impostare su `false`. Se l'attributo `type` non è impostato e `domElement` è impostato su `true`, IntelliSense considera il campo documentato come `HTMLElement` durante l'esecuzione del completamento delle istruzioni.

  `mayBeNull` Facoltativo. Specifica se il campo documentato può essere impostato su null. Impostare su `true` per indicare che il campo può essere impostato su null. in caso contrario, impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementType` Facoltativo. Se `type` è `Array`, questo attributo specifica il tipo degli elementi nella matrice.

  `elementInteger` Facoltativo. Se `type` è `Array` e `elementType` è `Number`, questo attributo specifica se gli elementi nella matrice sono numeri interi. Impostare su `true` per indicare che gli elementi della matrice sono numeri interi; in alternativa impostare su `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `elementDomElement` Facoltativo. Questo attributo è deprecato. L'attributo `elementType` ha la precedenza su questo attributo. Se `type` è `Array`, questo attributo specifica se gli elementi nella matrice sono elementi DOM. Impostare su `true` per specificare che gli elementi sono elementi DOM; in alternativa impostare su `false`. Se l'attributo `elementType` non è impostato e `elementDomElement` è `true`, IntelliSense considera ogni elemento della matrice come un elemento `HTMLElement` durante l'esecuzione del completamento istruzioni.

  `elementMayBeNull` Facoltativo. Se `type` è `Array`, specifica se gli elementi della matrice possono essere impostati su null. Impostare su `true` per indicare che gli elementi della matrice sono impostabili su null; in alternativa impostare su `false`. Il valore predefinito è `false`. Questo attributo non viene usato da Visual Studio per specificare informazioni IntelliSense.

  `helpKeyword` Facoltativo. Parola chiave per Guida F1.

  `locid` Facoltativo. Identificatore per le informazioni di localizzazione sul campo. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nel tag [\<loc>](../ide/loc-javascript.md).

  `value` Facoltativo. Specifica il codice che deve essere valutato per l'uso da parte di IntelliSense anziché dal codice della funzione stessa. Per `<field>`, questo attributo è supportato per le funzioni del costruttore, ma non è supportato per i valori letterali dell'oggetto. È possibile utilizzare questo attributo per fornire informazioni sul tipo quando il tipo di campo non è definito. Ad esempio, è possibile usare `value=’1’` per trattare il tipo di campo come numero.

  `description` Facoltativo. Una descrizione per il campo.

## <a name="remarks"></a>Osservazioni
 L'attributo `name` è obbligatorio quando si documenta un campo in una funzione del costruttore. Per tutti gli altri scenari, tutti gli attributi per l'elemento `<field>` sono facoltativi.

 Quando si documenta una funzione del costruttore, l'elemento `<field>` deve essere visualizzato immediatamente prima della dichiarazione di campo. L'attributo `name` deve corrispondere al nome del campo usato nel codice sorgente. Per i membri di un oggetto, l'attributo `name` può essere omesso se l'elemento `<field>` viene visualizzato immediatamente prima della dichiarazione del membro dell'oggetto.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<field>`.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare l'elemento `<field>` con l'attributo `static` impostato su `true`.

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare l'elemento `<field>` con l'attributo `static` impostato su `false`.

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare l'elemento `<field>` con l'attributo `value`.

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
