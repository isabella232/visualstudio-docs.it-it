---
title: IDebugFunctionPosition2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4811a6f2aa79e2e19524c0ea1e3e687cd7e28220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180913"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta una posizione astratta di una funzione in un documento di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per rappresentare la posizione di una funzione all'interno di un documento di origine.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene fornita come parte di un'Unione [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (in particolare, una struttura [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) ) che fa parte della struttura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , utilizzata per la creazione di un punto di interruzione in sospeso.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 La tabella seguente illustra i metodi di `IDebugFunctionPosition2` .  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ottiene il nome della funzione a cui è correlata questa posizione.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ottiene l'offset dall'inizio della funzione.|  
  
## <a name="remarks"></a>Osservazioni  
 La posizione rappresentata da questa interfaccia è basata su testo, in particolare una struttura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
