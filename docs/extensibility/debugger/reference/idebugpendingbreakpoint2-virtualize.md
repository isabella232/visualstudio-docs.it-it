---
title: IDebugPendingBreakpoint2::Virtualize . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ad5aac997cf694a7cf8fa887ae63fbef54ca07f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725663"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
Attiva/disattiva lo stato virtualizzato di questo punto di interruzione in sospeso. Quando un punto di interruzione in sospeso viene virtualizzato, il motore di debug tenterà di associarlo ogni volta che viene caricato nuovo codice nel programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Virtualize(
    BOOL fVirtualize
);
```

```cpp
int Virtualize(
    int fVirtualize
);
```

## <a name="parameters"></a>Parametri
`fVirtualize`\
[in] Impostare su`TRUE`diverso da zero ( ) per`FALSE`virtualizzare il punto di interruzione in sospeso o su zero ( ) per disattivare la virtualizzazione.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce un valore che `E_BP_DELETED` indica se il punto di interruzione è stato eliminato.

## <a name="remarks"></a>Osservazioni
Un punto di interruzione virtualizzato viene associato ogni volta che viene caricato il codice.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CPendingBreakpoint` implementare questo metodo per un oggetto semplice che espone il [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia.

```cpp
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        if (fVirtualize)
        {
            // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            SetFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
        else
        {
            // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
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
