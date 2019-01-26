---
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abda1b2544f93577f7355b60c07143c623da181e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931583"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Imposta il numero di passaggi per il punto di interruzione associato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetHitCount(   
   DWORD dwHitCount  
);  
```  
  
```csharp  
int SetHitCount(   
   uint dwHitCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwHitCount`  
 [in] Per impostare il numero di passaggi.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato viene impostato su `BPS_DELETED` (in parte il [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumerazione).  
  
## <a name="remarks"></a>Note  
 Il numero di passaggi è il numero di volte in cui che il punto di interruzione generato durante l'esecuzione della sessione corrente.  
  
 In genere, questo metodo viene chiamato dal motore di debug per aggiornare il numero di passaggi corrente su questo punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)