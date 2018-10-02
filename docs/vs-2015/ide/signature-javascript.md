---
title: '&lt;firma&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5b6172609b68e1800dd71b9367d93a52596e88cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517097"
---
# <a name="ltsignaturegt-javascript"></a>&lt;firma&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Raggruppa un set di elementi correlati per una funzione o un metodo per fornire documentazione per le funzioni in overload.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Parametri  
 `externalid`  
 Facoltativo. Se il `format` dell'attributo per il [ \<loc >](../ide/loc-javascript.md) elemento `vsdoc`, questo attributo specifica il membro ID usato per individuare il codice XML che è associati con la firma. A differenza di `locid` attributo, questo attributo specifica che tutti gli elementi nel membro con questo ID devono essere caricati. Anche le informazioni di descrizione associati presenti nel codice XML verranno unite con gli elementi specificati nella firma. In questo modo è possibile specificare elementi aggiuntivi, ad esempio `<capability>`, nel file sidecar senza specificarli nel file di origine. `externalid` è un attributo facoltativo.  
  
 `externalFile`  
 Facoltativo. Specifica il nome del file in cui trovare il `externalid`. Questo attributo viene ignorato se nessun `externalid` è presente. Si tratta di un attributo facoltativo. Il valore predefinito è il nome del file corrente ma con un'estensione di file di XML anziché. js. Per impostazione predefinita, le regole di ricerca di risorse gestite per la localizzazione vengono utilizzate per individuare il file.  
  
 `helpKeyword`  
 Facoltativo. La parola chiave per la Guida F1.  
  
 `locid`  
 Facoltativo. L'identificatore per le informazioni di localizzazione sul campo. L'identificatore è un membro ID o corrisponde alla `name` valore in un bundle di messaggio definito dai metadati OpenAjax dell'attributo. Il tipo di identificatore dipende dal formato specificato nella [ \<loc >](../ide/loc-javascript.md) tag.  
  
## <a name="remarks"></a>Note  
 Usare uno `<signature>` descrizione della funzione nel file con estensione js oppure usare uno di overload per ogni elemento `<signature>` (elemento) per ogni ID membro esterno specificato.  
  
 Il `<signature>` elemento deve essere inserito nel corpo della funzione prima di qualsiasi istruzione. Quando si usa [ \<riepilogo >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), oppure [ \<restituisce >](../ide/returns-javascript.md) gli elementi con la `<signature>` elemento, inserire gli altri elementi all'interno di `<signature>` blocco.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come utilizzare il `<signature>` elemento.  
  
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



