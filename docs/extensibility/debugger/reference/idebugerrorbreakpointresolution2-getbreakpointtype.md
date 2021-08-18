---
description: Ottiene il tipo di punto di interruzione.
title: IDebugErrorBreakpointResolution2::GetBreakpointType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44991f03a59e53fcdcee9d7fd163ac13635e51d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079085"
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
Ottiene il tipo di punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetBreakpointType(
    BP_TYPE* pBPType
);
```

```csharp
int GetBreakpointType(
    out enum_BP_TYPE pBPType
);
```

## <a name="parameters"></a>Parametri
`pBPType`\
[out] Restituisce un valore dall'enumerazione [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) che descrive il tipo di punto di interruzione.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Questo metodo restituisce il tipo del punto di interruzione che non è stato possibile associare, richiedendo quindi un evento di interruzione di errore.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto `CDebugErrorBreakpointResolution` semplice che espone [l'interfaccia IDebugErrorBreakpointResolution2.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)

```
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)
{
    HRESULT hr;

    if (pBPType)
    {
        // Set default BP_TYPE.
        *pBPType = BPT_NONE;

        // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.
        if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))
        {
            // Set the new BP_TYPE.
            *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;
            hr = S_OK;
        }
        else
        {
            hr = E_FAIL;
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
