---
title: '&lt;deprecato&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759756"
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
 `type`  
 Facoltativo. Specifica se la funzione o il metodo verrà rimosso in una versione futura, o se la funzione o metodo è già stato rimosso e che l'utilizzo può comportare un errore. Impostare su `deprecate` per specificare che la funzione o il metodo verrà rimosso in una versione futura. Impostare su `remove` per specificare che la funzione o metodo è già stato rimosso.  
  
 `locid`  
 Facoltativo. L'identificatore per le informazioni di localizzazione sulla funzione o al metodo. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `description`  
 Facoltativo. Descrizione della funzione o metodo che verrà deprecato.  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi utilizzati per annotare le funzioni, tra cui `<deprecated>`, deve essere inserito nel corpo della funzione prima di qualsiasi istruzione. Quando si contrassegna una funzione come deprecati, si consiglia di sostituire relativi [ \<riepilogo >](../ide/summary-javascript.md) elemento con la `<deprecated>` elemento.  
  
## <a name="example"></a>Esempio  
 Il codice seguente viene illustrato come utilizzare il `<deprecated>` elemento.  
  
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
