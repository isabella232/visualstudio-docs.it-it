---
title: Raggiungimento di un punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738575"
---
# <a name="hit-a-breakpoint"></a>Raggiungere un punto di interruzione
Nella sezione seguente viene descritto il processo quando il motore di debug (DE) raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di un'istruzione:

## <a name="troubleshoot-a-hit-breakpoint"></a>Risolvere i problemi relativi a un punto di interruzione

1. Il DE Invia un'interfaccia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) come **EVENT_SYNC_STOP**.

2. Il gestore di debug della sessione (SDM) chiama [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.

## <a name="see-also"></a>Vedere anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
