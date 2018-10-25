---
title: '&lt;campo&gt; (JavaScript) | Microsoft Docs'
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
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a57f84901f2ac6bc691c50fa6d1e3c8b94db6c50
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939906"
---
# <a name="ltfieldgt-javascript"></a>&lt;campo&gt; (JavaScript)
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
 `name`  
 Il nome del campo o membro. Quando la `<field>` elemento viene usato in una funzione del costruttore, `name` è obbligatorio e definisce il membro a cui viene applicato il tag. Quando il `<field>` elemento sta annotando direttamente un campo, questo attributo viene ignorato e il nome utilizzato da Visual Studio è il nome del campo effettivo nel codice sorgente.  
  
 `static`  
 Facoltativo. Specifica se il campo è un membro di funzione del costruttore o un membro dell'oggetto restituito dalla funzione del costruttore. Impostare su `true` trattare il campo come membro di funzione del costruttore. Impostare su `false` trattare il campo come membro dell'oggetto restituito dalla funzione del costruttore.  
  
 `type`  
 Facoltativo. Il tipo di dati del campo. Il tipo può essere uno dei seguenti:  
  
- Un linguaggio ECMAScript digitare nella specifica ECMAScript 5, ad esempio `Number` e `Object`.  
  
- Oggetto di un modello DOM, ad esempio `HTMLElement`, `Window`, e `Document`.  
  
- Funzione del costruttore JavaScript.  
  
  `integer`  
  Facoltativo. Se `type` è `Number`, specifica se il campo è un numero intero. Impostare su `true` per indicare che il campo è un numero intero; in caso contrario, impostato su `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
  `domElement`  
  Facoltativo. Questo attributo è deprecato. il `type` attributo ha la precedenza su questo attributo. Questo attributo specifica se il campo documentato è un elemento DOM. Impostare su `true` per specificare che il campo è un elemento DOM; in caso contrario, impostato su `false`. Se il `type` attributo non è impostato e `domElement` è impostata su `true`, IntelliSense considera il campo documentato come un `HTMLElement` durante l'esecuzione di completamento delle istruzioni.  
  
  `mayBeNull`  
  Facoltativo. Specifica se il campo documentato può essere impostato su null. Impostare su `true` per indicare che il campo può essere impostato su null; in caso contrario, impostato su `false`. Il valore predefinito è `false`. Questo attributo non viene utilizzato da Visual Studio per fornire informazioni di IntelliSense.  
  
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
  Facoltativo. L'identificatore per le informazioni di localizzazione sul campo. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) tag.  
  
  `value`  
  Facoltativo. Specifica il codice che deve essere valutato per l'uso da IntelliSense anziché il codice della funzione. Per `<field>`, questo attributo è supportato per le funzioni costruttore, ma non è supportato per i valori letterali di oggetto. È possibile usare questo attributo è per fornire informazioni sul tipo quando non è definito il tipo di campo. Ad esempio, è possibile usare `value=’1’` per considerare il tipo di campo sotto forma di numero.  
  
  `description`  
  Facoltativo. Una descrizione per il campo.  
  
## <a name="remarks"></a>Note  
 Il `name` attributo è obbligatorio quando si esegue la documentazione di un campo in una funzione del costruttore. Per tutti gli altri scenari, tutti gli attributi per il `<field>` elemento sono facoltativi.  
  
 Quando si esegue la documentazione di una funzione del costruttore, il `<field>` immediatamente prima della dichiarazione di campo deve essere presente l'elemento. Il `name` attributo deve corrispondere al nome di campo che viene usato nel codice sorgente. Per i membri di oggetto, il `name` attributo può essere omessa se la `<field>` elemento viene visualizzato immediatamente prima della dichiarazione di membro oggetto.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il `<field>` elemento.  
  
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
 Nell'esempio seguente viene illustrato come utilizzare il `<field>` elemento con il `static` attributo impostato su `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `<field>` elemento con il `static` attributo impostato su `false`.  
  
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
 Nell'esempio seguente viene illustrato come utilizzare il `<field>` elemento con la `value` attributo.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)



