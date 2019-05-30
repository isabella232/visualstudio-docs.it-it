---
title: Raggiungere un punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d95abd66f248ca994d7712f1bf51519022de9d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344050"
---
# <a name="hit-a-breakpoint"></a>Raggiungere un punto di interruzione
La sezione seguente descrive il processo quando il motore di debug (DE) raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di istruzioni:

## <a name="troubleshoot-a-hit-breakpoint"></a>Risolvere i problemi di un punto di interruzione hit

1. L'invio di DE un' [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) dell'interfaccia come un' **EVENT_SYNC_STOP**.

2. Gestore di sessione di debug (SDM) chiama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.

## <a name="see-also"></a>Vedere anche
- [Chiamare gli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)