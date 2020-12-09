---
title: Eventi di controllo | Microsoft Docs
description: Informazioni sull'invio di eventi durante l'esecuzione controllata del programma tramite l'interfaccia IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf7f59384d9317e4be173c93b6165d754a35ad8f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914244"
---
# <a name="control-events"></a>Eventi di controllo
È necessario inviare eventi durante l'esecuzione controllata del programma. Tutti gli eventi vengono inviati usando l'interfaccia [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) e hanno attributi che richiedono l'implementazione del metodo [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Metodi aggiuntivi
 Per alcuni eventi è richiesta l'implementazione di metodi aggiuntivi, come indicato di seguito:

- Per inviare l'interfaccia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) quando il motore di debug (de) viene inizializzato, è necessario implementare il metodo [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- Il controllo dell'esecuzione richiede l'implementazione di tali eventi di controllo come le interfacce [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** è obbligatorio solo per le interruzioni asincrone.

- Per l'esecuzione di funzioni è necessaria l'implementazione dell'interfaccia [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e dei relativi metodi.

  Gli eventi che derivano dai punti di interruzione richiedono l'implementazione delle interfacce [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , oltre ai metodi [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  Per la valutazione di espressioni asincrone è necessario implementare l'interfaccia [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) e i relativi metodi [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[e GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Per gli eventi sincroni è necessario implementare il metodo [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Affinché il motore scriva l'output di tipo stringa, è necessario implementare il metodo [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>Vedi anche
- [Controllo di esecuzione e valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)
