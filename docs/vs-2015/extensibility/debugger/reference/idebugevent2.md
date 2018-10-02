---
title: IDebugEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7fc387733e1472afe5f21f5e0638374ebda9f677
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540900"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugevent2).  
  
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

