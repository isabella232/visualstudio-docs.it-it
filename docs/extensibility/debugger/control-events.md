---
title: Eventi di controllo | Microsoft Docs
description: Informazioni sull'invio di eventi durante l'esecuzione controllata del programma tramite l'interfaccia IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5fe0f3d7bce5d7e29a87ec45da3968f65299254115b64ad16d16da6a665d03d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262958"
---
# <a name="control-events"></a>Eventi di controllo
È necessario inviare eventi durante l'esecuzione controllata del programma. Tutti gli eventi vengono inviati usando [l'interfaccia IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) e hanno attributi che richiedono l'implementazione del metodo [IDebugEvent2::GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Metodi aggiuntivi
 Alcuni eventi richiedono l'implementazione di metodi aggiuntivi, come indicato di seguito:

- [L'invio dell'interfaccia IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) quando viene inizializzato il motore di debug richiede l'implementazione del metodo [IDebugEngineCreateEvent2::GetEngine.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- Il controllo di esecuzione richiede l'implementazione di eventi di controllo come [le interfacce IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** è obbligatorio solo per le interruzioni asincrone.

- L'esecuzione di istruzioni nelle funzioni richiede l'implementazione [dell'interfaccia IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e dei relativi metodi.

  Gli eventi che derivano dai punti di interruzione richiedono l'implementazione delle interfacce [IDebugBreakpointErrorEvent2,](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) nonché dei metodi [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) ed [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  Per la valutazione asincrona delle espressioni è necessario implementare [l'interfaccia IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) e i relativi metodi [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[e GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Gli eventi sincroni richiedono l'implementazione del [metodo IDebugEngine2::ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Per scrivere un output di tipo stringa, è necessario implementare il metodo [IDebugOutputStringEvent2::GetString.](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)

## <a name="see-also"></a>Vedi anche
- [Controllo di esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
