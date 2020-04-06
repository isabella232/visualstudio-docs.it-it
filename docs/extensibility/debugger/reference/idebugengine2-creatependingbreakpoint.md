---
title: IDebugEngine2::CreatePendingBreakpoint . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731125"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crea un punto di interruzione in sospeso nel motore di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parametri
`pBPRequest`\
[in] Oggetto [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) che descrive il punto di interruzione in sospeso da creare.

`ppPendingBP`\
[fuori] Restituisce un [oggetto IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) che rappresenta il punto di interruzione in sospeso.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. In `E_FAIL` genere `pBPRequest` restituisce se il parametro non corrisponde `pBPRequest` a qualsiasi lingua supportata dal DE di se il parametro è non valido o incompleto.

## <a name="remarks"></a>Osservazioni
Un punto di interruzione in sospeso è essenzialmente una raccolta di tutte le informazioni necessarie per associare un punto di interruzione al codice. Il punto di interruzione in sospeso restituito da questo metodo non è associato al codice fino a quando il [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) metodo viene chiamato.

Per ogni punto di interruzione in sospeso impostato dall'utente, il gestore di sessione di debug (SDM) chiama questo metodo in ogni DE associato. Spetta al DE per verificare che il punto di interruzione è valido per i programmi in esecuzione in tale DE.

Quando l'utente imposta un punto di interruzione in una riga di codice, il DE è libero di associare il punto di interruzione alla riga più vicina nel documento che corrisponde a questo codice. Ciò consente all'utente di impostare un punto di interruzione nella prima riga di un'istruzione su più righe, ma associarlo nell'ultima riga (in cui tutto il codice viene attribuito nelle informazioni di debug).

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CProgram` implementare questo metodo per un oggetto semplice. L'implementazione del `IDebugEngine2::CreatePendingBreakpoint` DE di potrebbe quindi inoltrare tutte le chiamate a questa implementazione del metodo in ogni programma.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
