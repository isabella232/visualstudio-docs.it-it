---
title: IDebugExpressionContext2::ParseText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::ParseText
helpviewer_keywords:
- IDebugExpressionContext2::ParseText
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 170183924c31933f77903a89851c15c463c326e6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325905"
---
# <a name="idebugexpressioncontext2parsetext"></a>IDebugExpressionContext2::ParseText
Analizza un'espressione in formato testo per la valutazione successiva.

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
[in] L'espressione da analizzare.

`dwFlags`\
[in] Una combinazione di flag dal [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) enumerazione che controlla l'analisi.

`nRadix`\
[in] La radice da usare durante l'analisi di qualsiasi informazioni numeriche in `pszCode`.

`ppExpr`\
[out] Restituisce il [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) oggetto che rappresenta l'espressione analizzata, che è pronto per l'associazione e valutazione.

`pbstrError`\
[out] Restituisce il messaggio di errore se l'espressione contiene un errore.

`pichError`\
[out] Restituisce l'indice dei caratteri dell'errore nella `pszCode` se l'espressione contiene un errore.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
Quando viene chiamato questo metodo, un motore di debug (DE) deve analizzare l'espressione e convalida la correttezza. Il `pbstrError` e `pichError` parametri possono essere compilati se l'espressione non è valido.

Si noti che l'espressione non viene valutato, solo analizzato. Una chiamata successiva per la [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oppure [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metodi valuta l'espressione analizzata.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CEnvBlock` oggetto che espone il [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia. Questo esempio prende in considerazione l'espressione deve essere analizzato come nome di una variabile di ambiente e recupera il valore di tale variabile.

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

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
