---
description: Questo metodo converte una stringa di espressione in un'espressione analizzata.
title: IDebugExpressionEvaluator::P ass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 560274fa9364e86cbb689af2234f72397f0560fc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092163"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Questo metodo converte una stringa di espressione in un'espressione analizzata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parametri
`upstrExpression`\
in Stringa dell'espressione da analizzare.

`dwFlags`\
in Raccolta di costanti [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) che determinano il modo in cui l'espressione deve essere analizzata.

`nRadix`\
in Radice da usare per interpretare le informazioni numeriche.

`pbstrError`\
out Restituisce l'errore come testo leggibile.

`pichError`\
out Restituisce la posizione del carattere all'inizio dell'errore nella stringa dell'espressione.

`ppParsedExpression`\
out Restituisce l'espressione analizzata in un oggetto [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo produce un'espressione analizzata, non un valore effettivo. Un'espressione analizzata è pronta per essere valutata, ovvero convertita in un valore.

## <a name="see-also"></a>Vedi anche
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
