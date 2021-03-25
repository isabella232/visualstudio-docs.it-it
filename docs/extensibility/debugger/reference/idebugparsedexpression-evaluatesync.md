---
description: Questo metodo valuta l'espressione analizzata e, facoltativamente, esegue il cast del risultato a un altro tipo di dati.
title: 'IDebugParsedExpression:: EvaluateSync | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75f86506ea3cd29d09bf8c78a07eaabcf7a9a6f0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084636"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
Questo metodo valuta l'espressione analizzata e, facoltativamente, esegue il cast del risultato a un altro tipo di dati.

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
in Combinazione di costanti [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) che controllano la modalità di valutazione dell'espressione.

`dwTimeout`\
in Specifica il tempo massimo di attesa, in millisecondi, prima che venga restituito da questo metodo. Usare `INFINITE` per attendere per un periodo illimitato.

`pSymbolProvider`\
in Il provider di simboli, espresso come un'interfaccia [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .

`pAddress`\
in Il percorso di esecuzione corrente all'interno di un metodo, espresso come un'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pBinder`\
in Binder, espresso come un'interfaccia [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

`bstrResultType`\
in Tipo in cui deve essere eseguito il cast del risultato. Questo argomento può essere un valore null.

`ppResult`\
out Restituisce l'interfaccia [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che rappresenta i risultati della valutazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il contesto di valutazione dell'espressione è fornito da `pAddress` , che rende possibile determinare il metodo contenitore e quindi utilizzare le regole di ambito del linguaggio per determinare il valore dei simboli nell'espressione.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
