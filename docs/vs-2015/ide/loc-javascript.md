---
title: '&lt;Loc &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <loc> JavaScript XML tag
- loc JavaScript XML tag
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf6016b2c12fd5ebe7cfb76c14c776508d99d2db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651471"
---
# <a name="ltlocgt-javascript"></a>&lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica il percorso e il tipo del file sidecar che fornisce le informazioni di IntelliSense localizzate.

## <a name="syntax"></a>Sintassi

```
<loc filename="filename"
    format="vsdoc|messagebundle" />
```

#### <a name="parameters"></a>Parametri
 `filename` Facoltativo. Nome radice del file sidecar che contiene le informazioni di localizzazione per le impostazioni cultura non associate ad alcun paese. Quando Visual Studio cerca le informazioni di localizzazione, tenta di trovare una versione specifica delle impostazioni cultura di questo file. Se, ad esempio, `filename` è jquery.xml, Visual Studio cerca la cartella specifica delle impostazioni cultura corretta, ad esempio ja, nello stesso percorso del file js che contiene l' `<loc>` elemento. Se individua la cartella specifica delle impostazioni cultura, verifica se esiste un file di jquery.xml. Se non riesce a individuare il file corretto, USA invece le regole del percorso delle risorse gestite. Il valore predefinito per `filename` è il nome del file corrente, ma con estensione. XML anziché. js.

 `format` Facoltativo. Tipo di file sidecar usato per la localizzazione. Usare `messagebundle` per specificare l'uso dei bundle di messaggi definiti da metadati Ajax aperti. `messagebundle` è il formato consigliato. Questo formato, tuttavia, non è supportato in Microsoft AJAX o nei file con estensione winmd. Utilizzare `vsdoc` per specificare il formato di localizzazione .NET Framework standard utilizzato da Microsoft AJAX e Windows Runtime. Questo attributo è facoltativo. `vsdoc` è il formato predefinito.

## <a name="remarks"></a>Osservazioni
 L' `<loc>` elemento deve essere visualizzato nella parte superiore del file nella stessa sezione dell' `<reference>` elemento. Le regole di utilizzo per l' `<loc>` elemento sono le stesse dell' `<reference>` elemento. Per ulteriori informazioni, vedere la sezione "Direttive References" in [JavaScript IntelliSense](../ide/javascript-intellisense.md).

 Visual Studio elabora un singolo `<loc>` elemento per ogni file con estensione js. Se `<loc>` sono presenti più elementi, `<loc>` viene usato un solo elemento. Il comportamento per determinare l' `<loc>` elemento da usare non è definito.

 Quando si usa il formato di bundle dei messaggi, usare l' `locid` attributo nei commenti della documentazione XML per specificare il `name` valore dell'attributo.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come utilizzare l' `<loc>` elemento con il formato messagebundle. Aggiungere il codice XML seguente a un file denominato messageFilename.xml e inserire il file nella cartella specifica delle impostazioni cultura corretta, come specificato nella descrizione del `filename` parametro.

```
<?xml version="1.0" encoding="utf-8" ?>
<messagebundle>
  <msg name="1">A class that represents a rectangle</msg>
  <msg name="2">The height of a rectangle</msg>
  <msg name="3">The width of a rectangle</msg>
</messagebundle>

```

 Per l'esempio messagebundle, aggiungere il codice seguente a un file JavaScript nel progetto. L' `<loc>` elemento deve essere visualizzato come prima riga nel file JavaScript. Le descrizioni in questo codice verranno sostituite dalle descrizioni localizzate, se disponibili.

```javascript
/// <loc filename="messageFilename.xml" format="messagebundle"/>

function doSomething(a,b)
{
    /// <summary locid='1'>description</summary>
    /// <param name='a' locid='2'>parameter a description</param>
    /// <param name='b' locid='3'>parameter b description</param>
}

```

 Nell'esempio seguente viene usato il formato VSDoc. Aggiungere il codice XML seguente a un file denominato scriptFilename.xml e inserire il file nella cartella specifica delle impostazioni cultura corrette.

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

 Per l'esempio VSDoc, aggiungere il codice seguente a un file JavaScript nel progetto. Le descrizioni in questo codice verranno sostituite dalle descrizioni localizzate, se disponibili.

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
