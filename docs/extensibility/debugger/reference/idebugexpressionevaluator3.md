---
title: Proprietà IDebugExpressionEvaluator3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d25cd8cd4aec351df2a483e930bf469fbc086a68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729120"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Rappresenta un analizzatore di espressioni (EE) con una struttura ad albero del parser avanzata.

## <a name="syntax"></a>Sintassi

```
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2
```

## <a name="notes-for-callers"></a>Note per i chiamanti
 Questa versione del parser passa il provider di simboli e l'indirizzo del frame di valutazione.

## <a name="methods"></a>Metodi
 Oltre ai metodi sul IDebugExpressionEvaluator2 interfaccia, questa interfaccia implementa il metodo seguente:In addition to the methods on the [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interface, this interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Converte una stringa di espressione in un'espressione analizzata in base al provider di simboli e all'indirizzo del frame di valutazione.|

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
