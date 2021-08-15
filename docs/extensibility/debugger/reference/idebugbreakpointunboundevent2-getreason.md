---
description: Ottiene il motivo per cui il punto di interruzione è stato scollegato.
title: IDebugBreakpointUnboundEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7a621b03c235f59e8381418c8884c184808c91c1e8bdb009d6a569b90d378f6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262269"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
Ottiene il motivo per cui il punto di interruzione è stato scollegato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason
);
```

```csharp
int GetReason(
    out enum_ BP_UNBOUND_REASON pdwUnboundReason
);
```

## <a name="parameters"></a>Parametri
`pdwUnboundReason`\
[out] Restituisce un valore dall'enumerazione [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) che specifica il motivo per cui il punto di interruzione è stato scollegato.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
I motivi includono la riasserzione di un punto di interruzione in un percorso diverso dopo un'operazione di modifica e continuazione o la determinazione che un punto di interruzione è stato associato in errore.

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un **oggetto CBreakpointUnboundDebugEventBase** che espone l'interfaccia [IDebugBreakpointUnboundEvent2.](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)

```cpp
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(
    BP_UNBOUND_REASON* pdwUnboundReason)
{
    HRESULT hRes = E_FAIL;

    if ( EVAL(pdwUnboundReason) )
    {
        *pdwUnboundReason = m_dwReason;

        hRes = S_OK;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
