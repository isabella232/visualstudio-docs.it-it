---
description: Rappresenta una versione avanzata di un analizzatore di espressioni (edizione Enterprise).
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6910b41431442819cf7641ced3763cc3ab316217
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138510"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta una versione avanzata di un analizzatore di espressioni (edizione Enterprise).

## <a name="syntax"></a>Sintassi

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un analizzatore di espressioni.

## <a name="methods"></a>Metodi
 Oltre ai metodi [nell'interfaccia IDebugExpressionEvaluator,](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Recupera un oggetto servizio in base al relativo identificatore univoco.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Precarica i moduli designati dal provider di simboli specificato.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Consente all'analizzatore di espressioni (edizione Enterprise) di specificare l'interfaccia di callback che il motore del debugger (DE) userà per leggere le impostazioni delle metriche.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Imposta il percorso di Common Language Runtime (CLR) caricato nel debugger.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Consente a un motore di debug di passare un callback all'analizzatore di espressioni durante l'inizializzazione.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md).|Arresta e pulisce l'analizzatore di espressioni.|

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
