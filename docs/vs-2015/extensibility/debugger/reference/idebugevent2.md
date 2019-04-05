---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b4ffb4a9d8a0a7a63e895e1f47fc41139b7ba16
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967420"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per comunicare informazioni di debug critiche, ad esempio l'interruzione in corrispondenza di un punto di interruzione sia informazioni non critiche, ad esempio un messaggio di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) e il fornitore di porte personalizzato implementare questa interfaccia nello stesso oggetto come tutte le altre interfacce di eventi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Usando l'interfaccia argomento ID (IID) assegnato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), gestore di sessione di debug (SDM) chiama [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nel `IDebugEvent2` interfaccia per ottenere l'interfaccia di eventi appropriato.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ottiene gli attributi per questo evento di debug.|  
  
## <a name="remarks"></a>Note  
 Interfacce dell'evento più specifico, ad esempio [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), non derivano dall'interfaccia IDebugEvent2 ma vengono invece implementati come un'interfaccia separata sullo stesso oggetto come `IDebugEvent2`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
