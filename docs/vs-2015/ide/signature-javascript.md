---
title: '&lt;firma &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671124"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raggruppa un set di elementi correlati per una funzione o un metodo per fornire la documentazione per le funzioni in overload.

## <a name="syntax"></a>Sintassi

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Parametri
 `externalid` Facoltativo. Se l' `format` attributo per l' [\<loc>](../ide/loc-javascript.md) elemento è `vsdoc` , questo attributo specifica l'ID del membro usato per individuare il codice XML associato alla firma. Diversamente dall' `locid` attributo, questo attributo specifica che devono essere caricati tutti gli elementi del membro con questo ID. Tutte le informazioni di descrizione associate presenti nel codice XML verranno unite anche con gli elementi specificati nella firma. In questo modo è possibile specificare elementi aggiuntivi, ad esempio `<capability>` , nel file sidecar senza specificarli nel file di origine. `externalid` è un attributo facoltativo.

 `externalFile` Facoltativo. Specifica il nome del file in cui trovare `externalid` . Questo attributo viene ignorato se non `externalid` è presente alcun. Questo è un attributo facoltativo. Il valore predefinito è il nome del file corrente ma con estensione di file XML anziché js. Per impostazione predefinita, le regole di ricerca delle risorse gestite per la localizzazione vengono usate per individuare il file.

 `helpKeyword` Facoltativo. Parola chiave per Guida F1.

 `locid` Facoltativo. Identificatore per le informazioni di localizzazione sul campo. L'identificatore è un ID membro o corrisponde al valore dell'attributo `name` in un'aggregazione messaggi definita da metadati OpenAjax. Il tipo di identificatore dipende dal formato specificato nel [\<loc>](../ide/loc-javascript.md) tag.

## <a name="remarks"></a>Osservazioni
 Usare un `<signature>` elemento per ogni descrizione di funzione in overload nel file js oppure usare un `<signature>` elemento per ogni ID membro esterno specificato.

 L' `<signature>` elemento deve essere inserito nel corpo della funzione prima di qualsiasi istruzione. Quando si [\<summary>](../ide/summary-javascript.md) usano [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) gli elementi, o con l' `<signature>` elemento, inserire gli altri elementi all'interno del `<signature>` blocco.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come usare l'elemento `<signature>`.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>Vedere anche
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)
