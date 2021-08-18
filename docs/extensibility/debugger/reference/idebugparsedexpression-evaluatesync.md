---
description: Questo metodo valuta l'espressione analizzata e facoltativamente esegue il cast del risultato a un altro tipo di dati.
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 192ad990d0f5ad3a12fddc0cc9a56a5c92700d5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153277"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Questo metodo valuta l'espressione analizzata e facoltativamente esegue il cast del risultato a un altro tipo di dati.

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
[in] Combinazione di [costanti EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che controllano la modalità di valutazione dell'espressione.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per attendere per un periodo indefinito.

`pSymbolProvider`\
[in] Provider di simboli, espresso come [interfaccia IDebugSymbolProvider.](../../../extensibility/debugger/reference/idebugsymbolprovider.md)

`pAddress`\
[in] Posizione di esecuzione corrente all'interno di un metodo, espressa come [interfaccia IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

`pBinder`\
[in] Binder, espresso come interfaccia [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)

`bstrResultType`\
[in] Tipo di cui eseguire il cast del risultato. Questo argomento può essere un valore Null.

`ppResult`\
[out] Restituisce [l'interfaccia IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta i risultati della valutazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il contesto di valutazione dell'espressione viene fornito da , che consente di determinare il metodo contenitore e quindi di usare le regole di ambito del linguaggio per determinare il valore `pAddress` dei simboli nell'espressione.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
