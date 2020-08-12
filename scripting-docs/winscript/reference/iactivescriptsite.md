---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144662"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementato dall'host per creare un sito per il modulo di gestione di Windows script. In genere, il sito verrà associato al contenitore di tutti gli oggetti visibili allo script, ad esempio i controlli ActiveX. In genere, questo contenitore corrisponderà al documento o alla pagina visualizzata. Microsoft Internet Explorer, ad esempio, creerebbe un contenitore di questo tipo per ogni pagina HTML visualizzata. Ogni controllo ActiveX (o un altro oggetto di automazione) nella pagina e il motore di scripting stesso sarebbero enumerabili all'interno di questo contenitore.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera l'identificatore delle impostazioni locali utilizzato dall'host per visualizzare gli elementi dell'interfaccia utente.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ottiene informazioni su un elemento aggiunto a un motore tramite una chiamata al metodo [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una stringa definita dall'host che identifica in modo univoco la versione corrente del documento dal punto di vista dell'host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Chiamato quando l'esecuzione dello script è stata completata.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informa l'host che lo stato del motore di scripting è stato modificato.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informa l'host che si è verificato un errore di esecuzione durante l'esecuzione dello script da parte del motore.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informa l'host che il motore di script ha iniziato l'esecuzione del codice di script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informa l'host che il motore di scripting ha restituito l'esecuzione del codice di script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)