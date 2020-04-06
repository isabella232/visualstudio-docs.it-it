---
title: IDebugPendingBreakpoint2::Enable . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f796aef9533e3861a870b0a0543ae6b4aeb11de1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725899"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
Attiva/disattiva lo stato abilitato del punto di interruzione in sospeso.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Enable(
    BOOL fEnable
);
```

```csharp
int Enable(
    int fEnable
);
```

## <a name="parameters"></a>Parametri
`fEnable`\
[in] Impostare su`TRUE`diverso da zero ( ) per`FALSE`abilitare un punto di interruzione in sospeso o su zero ( ) per disabilitare.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce un valore che `E_BP_DELETED` indica se il punto di interruzione è stato eliminato.

## <a name="remarks"></a>Osservazioni
Quando un punto di interruzione in sospeso è abilitato o disabilitato, tutti i punti di interruzione associati da esso vengono impostati sullo stesso stato.

Questo metodo può essere chiamato tutte le volte che è necessario, anche se il punto di interruzione è già abilitato o disabilitato.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CPendingBreakpoint` implementare questo metodo per un oggetto semplice che espone il [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia.

```cpp
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        // If the bound breakpoint member variable is valid, then enable or
        // disable the bound breakpoint.
        if (m_pBoundBP)
        {
            m_pBoundBP->Enable(fEnable);
        }
        // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure
        // to enabled or disabled depending on the passed BOOL condition.
        m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;
        hr = S_OK;

    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
