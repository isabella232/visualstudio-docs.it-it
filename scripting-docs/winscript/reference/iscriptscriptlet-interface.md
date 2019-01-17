---
title: Interfaccia IScriptScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3b7c4af7769a1a2851e9be4e2639a324a3c06fb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345916"
---
# <a name="iscriptscriptlet-interface"></a>Interfaccia IScriptScriptlet
Un oggetto che implementa il `IScriptScriptlet` interfaccia rappresenta uno script di gestore dell'evento.  
  
 Oltre ai metodi ereditati da `IScriptEntry`, il `IScriptScriptlet` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Restituisce il nome dell'evento di cui è associato lo scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Restituisce il nome di evento semplice che è associato un scriptlet. Questo è un nome di singola parola che non contiene gli spazi vuoti.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Restituisce l'ultimo identificatore in specificare il nome completo dell'host dell'oggetto di scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Imposta il nome dell'evento di cui è associato lo scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Imposta il nome di evento semplice che è associato un scriptlet. Questo è un nome di singola parola che non contiene gli spazi vuoti.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Imposta l'ultimo identificatore nel nome completo dell'host dell'oggetto di scriptlet.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)