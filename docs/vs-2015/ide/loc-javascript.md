---
title: '&lt;loc&gt; (JavaScript) | Microsoft Docs'
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
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9314453b5e75e31f98d6989efa274278706bc5a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244010"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica il percorso e il tipo del file sidecar che fornisce informazioni di IntelliSense localizzate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### <a name="parameters"></a>Parametri  
 `filename`  
 Facoltativo. Il nome radice del file sidecar che contiene informazioni di localizzazione per le impostazioni cultura neutre. Quando Visual Studio cerca le informazioni di localizzazione, tenta di trovare una versione specifica della lingua di questo file. Ad esempio, se `filename` è jquery.xml, Visual Studio cerca la cartella specifica della lingua corretta (ad esempio JA) nello stesso percorso del file. js che contiene il `<loc>` elemento. Se individua la cartella di impostazioni cultura specifiche, verifica l'esistenza di un file jquery.xml in esso. Se non è possibile individuare il file corretto, ma usa le regole di percorso risorse gestite. Il valore predefinito per `filename` è il nome del file corrente, ma con estensione XML anziché. js.  
  
 `format`  
 Facoltativo. Il tipo di file sidecar utilizzato per la localizzazione. Usare `messagebundle` per specificare l'utilizzo di aggregazioni di messaggio definito dai metadati Ajax Open. `messagebundle` è il formato consigliato. Tuttavia, questo formato non è supportato in Microsoft Ajax o in file con estensione winmd. Usare `vsdoc` per specificare il formato di localizzazione .NET Framework standard che viene utilizzato da Microsoft Ajax e Windows Runtime. L'attributo è facoltativo. `vsdoc` rappresenta il formato predefinito.  
  
## <a name="remarks"></a>Note  
 Il `<loc>` deve essere presente l'elemento nella parte superiore del file nella stessa sezione di `<reference>` elemento. Le regole di utilizzo per il `<loc>` elemento sono gli stessi di `<reference>` elemento. Per altre informazioni, vedere la sezione "Riferimenti direttive" nella [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
 Visual Studio elabora un singolo `<loc>` (elemento) per ogni file con estensione js. Se più `<loc>` gli elementi sono presenti, solo una singola `<loc>` elemento viene usato. Comportamento per determinare a quali `<loc>` elemento da utilizzare non è definito.  
  
 Quando si usa il formato di bundle dei messaggi, usare il `locid` attributo nei commenti della documentazione XML per specificare il `name` valore dell'attributo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il `<loc>` elemento con formato messagebundle. Aggiungere il codice XML seguente in un file denominato messageFilename.xml e inserire il file nella cartella specifica della lingua corretta, come specificato nella descrizione del `filename` parametro.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 Nell'esempio messagebundle, aggiungere il codice seguente in un file JavaScript nel progetto. Il `<loc>` elemento deve essere visualizzato come la prima riga nel file JavaScript. Le descrizioni in questo codice verranno sostituite da localizzare le descrizioni, se disponibile.  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 L'esempio seguente usa il formato di VSDoc. Aggiungere il codice XML seguente in un file denominato scriptFilename.xml e inserire il file nella cartella specifica della lingua corretta.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 Nell'esempio di VSDoc, aggiungere il codice seguente in un file JavaScript nel progetto. Le descrizioni in questo codice verranno sostituite da localizzare le descrizioni, se disponibile.  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)



