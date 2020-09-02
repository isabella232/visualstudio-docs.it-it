---
title: '&lt;summary&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646853"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica la descrizione di una funzione o di un metodo.

## <a name="syntax"></a>Sintassi

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parametri
 `locid` Facoltativo. Identificatore per le informazioni di localizzazione sulla funzione o sul metodo. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nell' [\<loc>](../ide/loc-javascript.md) elemento.

 `description` Facoltativo. Descrizione della funzione o del metodo.

## <a name="remarks"></a>Osservazioni
 Gli elementi utilizzati per aggiungere annotazioni alle funzioni, tra cui [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) e [\<returns>](../ide/returns-javascript.md) , devono essere inseriti nel corpo della funzione prima di qualsiasi istruzione.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<summary>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
