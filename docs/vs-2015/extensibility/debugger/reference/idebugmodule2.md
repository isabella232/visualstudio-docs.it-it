---
title: IDebugModule2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92e11532019caf5aa7af3c84f7222fdfabcfa45d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768545"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un modulo, vale a dire, un'unità di un programma eseguibile, ad esempio una DLL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare un modulo e per fornire l'accesso alle informazioni su tale modulo.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Una chiamata a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) restituisce questa interfaccia. L'invia DE il [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interfaccia per la gestione di debug di sessione (SDM) usando la [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (metodo).  
  
 Questa interfaccia può anche essere restituita un [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struttura (che viene restituito da una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Successivo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce anche questa interfaccia ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) restituisce il [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugModule2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ottiene il [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) che descrive questo modulo.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NON USARE. Ricarica i simboli per questo modulo.|  
  
## <a name="remarks"></a>Note  
 Informazioni sul modulo possono essere visualizzati nei **moduli** finestra dell'IDE.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

