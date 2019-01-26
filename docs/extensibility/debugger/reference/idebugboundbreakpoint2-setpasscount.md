---
title: IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f8285b0a348809d6eed972f87ea36958b76d086
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944647"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Imposta o modifica il numero di sessione associato a questo punto di interruzione associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `bpPassCount`  
 [in] Il [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) struttura che specifica il conteggio di pass.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato viene impostato su `BPS_DELETED` (in parte il [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumerazione).  
  
## <a name="remarks"></a>Note  
 Il conteggio pass determina quando viene attivato il punto di interruzione. Il passaggio corrente o il numero di passaggi può essere ottenuto chiamando il [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) (metodo).  
  
 Qualsiasi numero di passaggio che era precedentemente associato a questo punto di interruzione viene perso.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)