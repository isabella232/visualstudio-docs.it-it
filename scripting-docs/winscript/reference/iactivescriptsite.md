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
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152642"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementato dall'host per creare un sito per il motore di Script di Windows. In genere, questo sito sarà associato al contenitore di tutti gli oggetti che sono visibili allo script (ad esempio, i controlli ActiveX). In genere, questo contenitore corrisponderà al documento o pagina che viene visualizzato. Microsoft Internet Explorer, ad esempio, sarebbe creare tali un contenitore per ogni pagina HTML viene visualizzata. Ogni ActiveX controllo (o un altro oggetto di automazione) nella pagina e il motore di scripting, sarebbe enumerabile all'interno del contenitore.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera l'identificatore delle impostazioni locali usato dall'host per la visualizzazione di elementi dell'interfaccia utente.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ottiene informazioni su un elemento che è stato aggiunto a un motore tramite una chiamata per il [IActiveScript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) (metodo).|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una stringa definita dall'host che identifica in modo univoco la versione corrente del documento dal punto di vista dell'host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Chiamato al termine dell'esecuzione dello script.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Comunica all'host che il motore di script è stato modificato gli stati.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Comunica all'host che si è verificato un errore di esecuzione mentre il motore è stato eseguito lo script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Comunica all'host che il motore di scripting è iniziata l'esecuzione del codice di script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Comunica all'host che il motore di script ha restituito dall'esecuzione di codice di script.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)