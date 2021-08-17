---
description: Ottiene un oggetto IDebugErrorBreakpoint2 che descrive il motivo per cui un punto di interruzione non è stato associato.
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a90e63e234da8b68f233cde19034cce9f382faaf56ee0d44d41c12275f631fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417561"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
Ottiene un oggetto [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) che descrive il motivo per cui un punto di interruzione non è stato associato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetErrorBreakpoint( 
    IDebugErrorBreakpoint2** ppErrorBP
);
```

```csharp
int GetErrorBreakpoint( 
    out IDebugErrorBreakpoint2 ppErrorBP
);
```

## <a name="parameters"></a>Parametri
`ppErrorBP`\
[out] Restituisce un [oggetto IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) che descrive l'avviso o l'errore.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Dopo aver `IDebugErrorBreakpoint2` ottenuto l'interfaccia, chiamare il [metodo GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) per ottenere un [oggetto IDebugErrorBreakpointResolution2.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) È quindi possibile usare il metodo [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) per determinare una posizione non valida, un'espressione non valida o i motivi per cui il punto di interruzione in sospeso non è stato associato, ad esempio il codice non ancora caricato e così via.

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un oggetto **CBreakpointSetDebugEventBase** che espone [l'interfaccia IDebugBreakpointErrorEvent2.](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)

```cpp
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(
    IDebugErrorBreakpoint2 **ppbp)
{
    HRESULT hRes = E_FAIL;

    if ( ppbp )
    {
        if ( m_pError )
        {
            *ppbp = m_pError;

            m_pError->AddRef();

            hRes = S_OK;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
