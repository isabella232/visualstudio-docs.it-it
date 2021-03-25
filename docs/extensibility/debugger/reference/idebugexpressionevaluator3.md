---
description: Rappresenta un analizzatore di espressioni (EE) con un albero del parser migliorato.
title: IDebugExpressionEvaluator3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab5264b888de6763d54f561bea5c9a7d34002b0a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077291"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un analizzatore di espressioni (EE) con un albero del parser migliorato.

## <a name="syntax"></a>Sintassi

```
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa versione del parser passa il provider di simboli e l'indirizzo del frame di valutazione.

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) , questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Converte una stringa di espressione in un'espressione analizzata in base al provider di simboli e all'indirizzo del frame di valutazione.|

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
