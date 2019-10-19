---
title: Interfaccia IScriptScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571880"
---
# <a name="iscriptscriptlet-interface"></a>Interfaccia IScriptScriptlet
Un oggetto che implementa l'interfaccia `IScriptScriptlet` rappresenta uno script del gestore eventi.  
  
 Oltre ai metodi ereditati da `IScriptEntry`, l'interfaccia `IScriptScriptlet` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Restituisce il nome dell'evento associato a scriptlet.|  
|[IScriptScriptlet::GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Restituisce il nome semplice dell'evento associato a un scriptlet. Si tratta di un nome costituito da una sola parola che non contiene spazi vuoti.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Restituisce l'ultimo identificatore nel nome completo dell'host oggetto di un scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Imposta il nome dell'evento associato a scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Imposta il nome dell'evento semplice associato a un scriptlet. Si tratta di un nome costituito da una sola parola che non contiene spazi vuoti.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Imposta l'ultimo identificatore nel nome completo dell'host oggetto di un scriptlet.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)