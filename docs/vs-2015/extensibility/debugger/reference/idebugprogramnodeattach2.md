---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 580d4d2432a957bae8c590b3590a11b1a0b5e84e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148533"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Consente a un nodo del programma di ricevere una notifica di un tentativo di connessione al programma associato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Questa interfaccia viene implementata nella stessa classe che implementa l'interfaccia [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) per ricevere una notifica di un'operazione di connessione e per offrire l'opportunità di annullare l'operazione di associazione.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Ottenere questa interfaccia chiamando il `QueryInterface` metodo in un oggetto [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Il metodo [Onconnettit](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) deve essere chiamato prima del metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) per fornire al nodo del programma la possibilità di arrestare il processo di connessione.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Si connette al programma associato o rinvia il processo di associazione al metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia è l'alternativa preferita al metodo [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) deprecato. Tutti i motori di debug vengono sempre caricati con la `CoCreateInstance` funzione, ovvero ne viene creata un'istanza fuori dallo spazio degli indirizzi del programma di cui è in corso il debug.  
  
 Se un'implementazione precedente del `IDebugProgramNode2::Attach_V7` Metodo stava semplicemente impostando il `GUID` del programma di cui è in corso il debug, è necessario implementare solo il metodo [onconnettit](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
 Se un'implementazione precedente del `IDebugProgramNode2::Attach_V7` Metodo usava l'interfaccia di callback fornita, la funzionalità deve essere spostata in un'implementazione del metodo di [connessione](../../../extensibility/debugger/reference/idebugengine2-attach.md) e `IDebugProgramNodeAttach2` non è necessario implementare l'interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
