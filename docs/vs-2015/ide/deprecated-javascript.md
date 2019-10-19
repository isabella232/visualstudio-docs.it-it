---
title: '&lt;deprecated &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665809"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica una funzione o un metodo deprecato.

## <a name="syntax"></a>Sintassi

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parametri
 `type` Facoltativo. Specifica se la funzione o il metodo verrà rimosso in una versione futura o se la funzione o il metodo è già stato rimosso e se il relativo utilizzo può causare un errore. Impostare su `deprecate` per specificare che la funzione o il metodo verrà rimosso in una versione futura. Impostare su `remove` per specificare che la funzione o il metodo è già stato rimosso.

 `locid` Facoltativo. Identificatore per le informazioni di localizzazione sulla funzione o sul metodo. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nell'elemento [\<loc>](../ide/loc-javascript.md).

 `description` Facoltativo. Descrizione della funzione o del metodo deprecato.

## <a name="remarks"></a>Osservazioni
 Gli elementi utilizzati per annotare le funzioni che includono `<deprecated>` devono essere inseriti nel corpo della funzione prima di qualsiasi istruzione. Quando si contrassegna una funzione come deprecata, è consigliabile sostituire la relativa [\<summary elemento >](../ide/summary-javascript.md) con l'elemento `<deprecated>`.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<deprecated>`.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
