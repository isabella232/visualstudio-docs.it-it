---
title: Proprietà IDebugParsedExpression::EvaluateSync . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f00b209ff5f91d160e89f5f55ad966fbe9e6414
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726017"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Questo metodo valuta l'espressione analizzata e facoltativamente esegue il cast del risultato in un altro tipo di dati.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EvaluateSync( 
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugSymbolProvider* pSymbolProvider,
   IDebugAddress*        pAddress,
   IDebugBinder*         pBinder,
   BSTR                  bstrResultType,
   IDebugProperty2**     ppResult
);
```

```csharp
int EvaluateSync(
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   IDebugSymbolProvider pSymbolProvider,
   IDebugAddress        pAddress,
   IDebugBinder         pBinder,
   string               bstrResultType,
   out IDebugProperty2  ppResult
);
```

## <a name="parameters"></a>Parametri
`dwEvalFlags`\
[in] Combinazione di costanti [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che controllano il modo in cui l'espressione deve essere valutata.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Utilizzare `INFINITE` per attendere a tempo indeterminato.

`pSymbolProvider`\
[in] Provider di simboli, espresso come [un IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia.

`pAddress`\
[in] Posizione di esecuzione corrente all'interno di un metodo, espressa come [un IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.

`pBinder`\
[in] Il gestore di associazione, espresso come [un IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia.

`bstrResultType`\
[in] Tipo in cui deve essere eseguito il cast del risultato. Questo argomento può essere un valore null.

`ppResult`\
[fuori] Restituisce il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta i risultati della valutazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il contesto di `pAddress`valutazione dell'espressione è dato da , che consente di determinare il metodo contenitore e quindi utilizzare le regole di ambito del linguaggio per determinare il valore dei simboli nell'espressione.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
