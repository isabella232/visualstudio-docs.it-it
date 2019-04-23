---
title: Raggiungere un punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1286af8222703028d5a8a1bd2dbb0d990ca7e30c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041093"
---
# <a name="hit-a-breakpoint"></a>Raggiungere un punto di interruzione
La sezione seguente descrive il processo quando il motore di debug (DE) raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di istruzioni:

## <a name="troubleshoot-a-hit-breakpoint"></a>Risolvere i problemi di un punto di interruzione hit

1. L'invio di DE un' [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) dell'interfaccia come un' **EVENT_SYNC_STOP**.

2. Gestore di sessione di debug (SDM) chiama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.

## <a name="see-also"></a>Vedere anche
- [Chiamare gli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)