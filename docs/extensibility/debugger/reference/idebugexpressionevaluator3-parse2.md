---
description: Converte una stringa di espressione in un'espressione analizzata in base al provider di simboli e all'indirizzo del frame di valutazione.
title: IDebugExpressionEvaluator3::P arse2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a10db1315249a78ebbc786dec3e54da92532ba7262294490c76c145c9a11fc6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360391"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Converte una stringa di espressione in un'espressione analizzata in base al provider di simboli e all'indirizzo del frame di valutazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Parse2 (
    LPCOLESTR                upstrExpression,
    PARSEFLAGS               dwFlags,
    UINT                     nRadix,
    IDebugSymbolProvider*    pSymbolProvider,
    IDebugAddress*           pAddress,
    BSTR*                    pbstrError,
    UINT*                    pichError,
    IDebugParsedExpression** ppParsedExpression
);
```

```csharp
HRESULT Parse2 (
    string                     upstrExpression,
    enum_PARSEFLAGS            dwFlags,
    uint                       nRadix,
    IDebugSymbolProvider       pSymbolProvider,
    IDebugAddress              pAddress,
    out string                 pbstrError,
    out uint                   pichError,
    out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parametri
`upstrExpression`\
[in] Stringa dell'espressione da analizzare.

`dwFlags`\
[in] Raccolta di costanti [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) che determinano la modalità di analisi dell'espressione.

`nRadix`\
[in] Radice da usare per interpretare qualsiasi informazione numerica.

`pSymbolProvider`\
[in] Interfaccia del provider di simboli.

`pAddress`\
[in] Indirizzo del frame di valutazione.

`pbstrError`\
[out] Restituisce l'errore come testo leggibile.

`pichError`\
[out] Restituisce la posizione del carattere dell'inizio dell'errore nella stringa dell'espressione.

`ppParsedExpression`\
[out] Restituisce l'espressione analizzata in un [oggetto IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md)

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Questo metodo produce un'espressione analizzata, non un valore effettivo. Un'espressione analizzata è pronta per essere valutata, ad esempio convertita in un valore .

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto **CEE** che espone [l'interfaccia IDebugExpressionEvaluator3.](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)

```cpp
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,
  PARSEFLAGS in_FLAGS,
  UINT in_RADIX,
  IDebugSymbolProvider *pSymbolProvider,
  IDebugAddress *pAddress,
  BSTR* out_pbstrError,
  UINT* inout_pichError,
  IDebugParsedExpression** out_ppParsedExpression )
{
    // precondition
    REQUIRE( NULL != in_szExprText );
    //REQUIRE( NULL != out_pbstrError );
    REQUIRE( NULL != inout_pichError );
    REQUIRE( NULL != out_ppParsedExpression );

    if (NULL == in_szExprText)
        return E_INVALIDARG;

    if (NULL == inout_pichError)
        return E_POINTER;

    if (NULL == out_ppParsedExpression)
        return E_POINTER;

    if (out_pbstrError)
        *out_pbstrError = NULL;

    *out_ppParsedExpression = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    // function body
    EEDomain::fParseExpression DomainVal =
    {
        this,                   // CEE*
        in_szExprText,          // LPCOLESTR
        in_FLAGS,               // EVALFLAGS
        in_RADIX,               // RADIX
        out_pbstrError,         // BSTR*
        inout_pichError,        // UINT*
        pSymbolProvider,
        out_ppParsedExpression  // Output
    };

    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
