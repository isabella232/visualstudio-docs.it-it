---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d49c912ae14154fc552c76fc011596f4f22166f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153569"
---
# <a name="bp_condition"></a>BP_CONDITION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrive le condizioni in cui un punto di interruzione viene attivato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```csharp  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## <a name="members"></a>Membri  
 `pThread`  
 Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread attivo per l'applicazione che contiene il punto di interruzione.  
  
 `styleCondition`  
 Valore dell'enumerazione [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) che descrive lo stile di questa condizione del punto di interruzione.  
  
 `bstrContext`  
 Posizione del punto di interruzione.  
  
 `bstrCondition`  
 Condizione di attivazione del punto di interruzione.  
  
 `nRadix`  
 Radice da usare per la valutazione di qualsiasi informazione numerica.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura è un membro delle strutture [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 Questa struttura viene passata anche come parametro ai metodi [secondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) e [secondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [Condizione di](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [Condizione di](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
