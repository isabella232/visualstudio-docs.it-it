---
title: IDebugExpression2::EvaluateSync Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729680"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Questo metodo valuta l'espressione in modo sincrono.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EvaluateSync(
    EVALFLAGS             dwFlags,
    DWORD                 dwTimeout,
    IDebugEventCallback2* pExprCallback,
    IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
    enum_EVALFLAGS       dwFlags,
    uint                 dwTimeout,
    IDebugEventCallback2 pExprCallback,
    out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametri
`dwFlags`\
[in] Combinazione di flag dell'enumerazione [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che controllano la valutazione dell'espressione.

`dwTimeout`\
[in] Tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per attendere a tempo indeterminato.

`pExprCallback`\
[in] Questo parametro è sempre un valore null.

`ppResult`\
[fuori] Restituisce l'oggetto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che contiene il risultato della valutazione dell'espressione.

## <a name="return-value"></a>Valore restituito
Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce un codice di errore. Alcuni codici di errore tipici sono:

|Errore|Descrizione|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|È attualmente in fase di valutazione un'altra espressione e la valutazione simultanea dell'espressione non è supportata.|
|E_EVALUATE_TIMEOUT|Timeout della valutazione.|

## <a name="remarks"></a>Osservazioni
Per la valutazione sincrona, non è necessario inviare un evento a Visual Studio al completamento della valutazione.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CExpression` implementare questo metodo per un oggetto semplice che implementa il [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfaccia.

```cpp
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,
                                  DWORD dwTimeout,
                                  IDebugEventCallback2* pExprCallback,
                                  IDebugProperty2** ppResult)
{
    // Set the aborted state to FALSE.
    m_bAborted = FALSE;
    // Delegate the evaluation to EvalExpression.
    return EvalExpression(TRUE, ppResult);
}

HRESULT CExpression::EvalExpression(BOOL bSynchronous,
                                    IDebugProperty2** ppResult)
{
    HRESULT hr;

    // Get the value of an environment variable.
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);
    // Create and initialize a CEnvVar object with the retrieved value.
    // CEnvVar implements the IDebugProperty2 interface.
    CComObject<CEnvVar> *pEnvVar;
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);

    if (pszVal) {
        // Check for synchronous evaluation.
        if (bSynchronous) {
            // Set and AddRef the result, IDebugProperty2 interface.
            *ppResult = pEnvVar;
            (*ppResult)->AddRef();
            hr = S_OK;
        } else {
            //For asynchronous evaluation, send an evaluation complete event.
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);
        }
    } else {
        // If a valid value is not retrieved, return E_FAIL.
        hr = E_FAIL;
    }
    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
