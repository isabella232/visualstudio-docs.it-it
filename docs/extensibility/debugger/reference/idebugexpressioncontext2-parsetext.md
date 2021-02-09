---
title: IDebugExpressionContext2::P arseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc55cceb8db392d590ff414ac3df5b807d1e52e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901649"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analizza un'espressione in formato testo per una valutazione successiva.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2** ppExpr,
    BSTR*               pbstrError,
    UINT*               pichError
);
```

```csharp
int ParseText(
    string                pszCode,
    enum_PARSEFLAGS       dwFlags,
    uint                  nRadix,
    out IDebugExpression2 ppExpr,
    out string            pbstrError,
    out uint              pichError
);
```

## <a name="parameters"></a>Parametri
`pszCode`\
in Espressione da analizzare.

`dwFlags`\
in Combinazione di flag dell'enumerazione [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) che controlla l'analisi.

`nRadix`\
in La radice da utilizzare per l'analisi di qualsiasi informazione numerica in `pszCode` .

`ppExpr`\
out Restituisce l'oggetto [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) che rappresenta l'espressione analizzata, pronta per l'associazione e la valutazione.

`pbstrError`\
out Restituisce il messaggio di errore se l'espressione contiene un errore.

`pichError`\
out Restituisce l'indice dei caratteri dell'errore in `pszCode` se l'espressione contiene un errore.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Quando viene chiamato questo metodo, un motore di debug (DE) deve analizzare l'espressione e convalidarla per verificarne la correttezza. `pbstrError` `pichError` Se l'espressione non è valida, è possibile compilare i parametri e.

Si noti che l'espressione non viene valutata, solo analizzata. Una chiamata successiva ai metodi [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) valuta l'espressione analizzata.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un `CEnvBlock` oggetto semplice che espone l'interfaccia [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Questo esempio considera l'espressione da analizzare come nome di una variabile di ambiente e recupera il valore da tale variabile.

```cpp
HRESULT CEnvBlock::ParseText(
    LPCOLESTR           pszCode,
    PARSEFLAGS          dwFlags,
    UINT                nRadix,
    IDebugExpression2 **ppExpr,
    BSTR               *pbstrError,
    UINT               *pichError)
{
    HRESULT hr = E_OUTOFMEMORY;
    // Create an integer variable with a value equal to one plus
    // twice the length of the passed expression to be parsed.
    int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;
    // Allocate a character string of the same length.
    char *pszAnsiCode = (char *) malloc(iAnsiLen);

    // Check for successful memory allocation.
    if (pszAnsiCode) {
        // Map the wide-character pszCode string to the new pszAnsiCode character string.
        WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);
        // Check to see if the app can succesfully get the environment variable.
        if (GetEnv(pszAnsiCode)) {

            // Create and initialize a CExpression object.
            CComObject<CExpression> *pExpr;
            CComObject<CExpression>::CreateInstance(&pExpr);
            pExpr->Init(pszAnsiCode, this, NULL);

            // Assign the pointer to the new object to the passed argument
            // and AddRef the object.
            *ppExpr = pExpr;
            (*ppExpr)->AddRef();
            hr = S_OK;
        // If the program cannot succesfully get the environment variable.
        } else {
            // Set the errror message and return E_FAIL.
            *pbstrError = SysAllocString(L"No such environment variable.");
            hr = E_FAIL;
        }
        // Free the local character string.
        free(pszAnsiCode);
    }
    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
