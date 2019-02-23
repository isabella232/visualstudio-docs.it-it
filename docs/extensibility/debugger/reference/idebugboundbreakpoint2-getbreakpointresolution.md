---
title: IDebugBoundBreakpoint2::GetBreakpointResolution | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1e3e4cfe144713b7747f74e754a3a265cbbdb15
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712164"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Ottiene la risoluzione di punto di interruzione che descrive il punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetBreakpointResolution( 
    IDebugBreakpointResolution2** ppBPResolution
);
```

```csharp
int GetBreakpointResolution( 
    out IDebugBreakpointResolution2 ppBPResolution
);
```

#### <a name="parameters"></a>Parametri
`ppBPResolution`

 [out] Restituisce il [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfaccia che rappresenta uno dei seguenti:

- L'oggetto di risoluzione dei punti di interruzione che descrive la posizione nel codice in cui è stato associato un punto di interruzione del codice.

- Il percorso dei dati in cui è associato un punto di interruzione dei dati.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce `E_BP_DELETED` se lo stato dell'oggetto punto di interruzione associato viene impostato su `BPS_DELETED` (in parte il [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumerazione).

## <a name="remarks"></a>Note
Chiamare il [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) metodo per determinare se la risoluzione del punto di interruzione per dati o codice.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CBoundBreakpoint` oggetto che espone il [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaccia.

```
HRESULT CBoundBreakpoint::GetBreakpointResolution(
    IDebugBreakpointResolution2** ppBPResolution)
{
    HRESULT hr;

    if (ppBPResolution)
    {
        // Verify that the bound breakpoint has not been deleted. If
        // deleted, then return hr = E_BP_DELETED.
        if (m_state != BPS_DELETED)
        {
            // Query for the IDebugBreakpointResolution2 interface.
            hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,
                                          (void **)ppBPResolution);
            assert(hr == S_OK);
        }
        else
        {
            hr = E_BP_DELETED;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
