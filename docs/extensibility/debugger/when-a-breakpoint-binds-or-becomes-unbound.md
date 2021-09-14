---
title: Quando un punto di interruzione viene associato o diventa | Microsoft Docs
description: Informazioni sui punti di interruzione non associati. Quando non è possibile associare un punto di interruzione nel momento in cui viene effettuata una chiamata, l'ora di associazione e l'ora di creazione del punto di interruzione sono diverse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a2373497f56f1c689de12bdd72e55fba84f51cc5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626315"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quando un punto di interruzione viene associato o non associato
Quando non è possibile associare un punto di interruzione nel momento in cui viene effettuata una chiamata al metodo [IDebugPendingBreakpoint2::CanBind,](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) l'ora di associazione e l'ora di creazione del punto di interruzione sono diverse.

## <a name="methods-called"></a>Metodi chiamati
 Gestione debug sessione (SDM) chiama i metodi seguenti:

1. [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). De restituisce un [oggetto IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

2. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. Il [metodo IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) e restituisce S_OK. IL DE invia un [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. [Metodi IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) per verificare e ottenere i punti di interruzione associati.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
