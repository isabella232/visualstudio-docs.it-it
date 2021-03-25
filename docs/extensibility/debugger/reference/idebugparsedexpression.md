---
description: Questa interfaccia rappresenta un'espressione analizzata pronta per la valutazione.
title: IDebugParsedExpression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 00daeac20d621657d61aa802d79a46a3ee0e7aa7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084584"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Questa interfaccia rappresenta un'espressione analizzata pronta per la valutazione.

## <a name="syntax"></a>Sintassi

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un analizzatore di espressioni implementa questa interfaccia per rappresentare un'espressione analizzata pronta per la valutazione.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Una chiamata a [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) restituisce questa interfaccia.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente viene illustrato il metodo di `IDebugParsedExpression` .

|Metodo|Descrizione|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Valuta l'espressione analizzata.|

## <a name="remarks"></a>Commenti
 Quando il chiamante è pronto per la valutazione dell'espressione, chiama [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) per restituire un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che contiene il risultato della valutazione. Questo approccio in due parti per la valutazione, l'analisi e la valutazione di, consente di valutare l'espressione analizzata più volte, ignorando il processo che richiede molto tempo per l'analisi dell'espressione.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md).
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
