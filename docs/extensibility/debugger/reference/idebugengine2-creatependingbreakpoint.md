---
description: Crea un punto di interruzione in sospeso nel motore di debug.
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31a138104cbaeea8eb0a2313956f5d1bba34db28
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711934"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Crea un punto di interruzione in sospeso nel motore di debug.

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
[out] Restituisce un oggetto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) che rappresenta il punto di interruzione in sospeso.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. In genere `E_FAIL` restituisce se il parametro non corrisponde ad alcun linguaggio supportato da DE di se il parametro non è valido o `pBPRequest` `pBPRequest` incompleto.

## <a name="remarks"></a>Commenti
Un punto di interruzione in sospeso è essenzialmente una raccolta di tutte le informazioni necessarie per associare un punto di interruzione al codice. Il punto di interruzione in sospeso restituito da questo metodo non è associato al codice fino a quando non [viene chiamato](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) il metodo Bind.

Per ogni punto di interruzione in sospeso impostato dall'utente, lo SDM (Session Debug Manager) chiama questo metodo in ogni deallegato. È necessario verificare che il punto di interruzione sia valido per i programmi in esecuzione in tale DE.

Quando l'utente imposta un punto di interruzione in una riga di codice, de è libero di associare il punto di interruzione alla riga più vicina nel documento che corrisponde a questo codice. In questo modo l'utente può impostare un punto di interruzione nella prima riga di un'istruzione su più righe, ma associarlo all'ultima riga (in cui tutto il codice è attribuito nelle informazioni di debug).

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto `CProgram` semplice. L'implementazione di DE di `IDebugEngine2::CreatePendingBreakpoint` potrebbe quindi inoltrare tutte le chiamate a questa implementazione del metodo in ogni programma.

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

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
