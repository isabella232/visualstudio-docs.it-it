---
title: IDebugPendingBreakpoint2::GetState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc5455424070d475d3c26f91a18ffebf0cc6747d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721966"
---
# <a name="idebugpendingbreakpoint2getstate"></a>IDebugPendingBreakpoint2::GetState
Ottiene lo stato del punto di interruzione in sospeso.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetState( 
   PENDING_BP_STATE_INFO* pState
);
```

```csharp
int GetState( 
   PENDING_BP_STATE_INFO[] pState
);
```

#### <a name="parameters"></a>Parametri
 `pState`

 [in, out] Oggetto [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) struttura compilata con una descrizione di questo oggetto in sospeso punto di interruzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)