---
title: Creazione di un punto di interruzione . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d252f1310c3e251c44525cd94c4d9a2943d8171d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739047"
---
# <a name="create-a-breakpoint"></a>Creare un punto di interruzioneCreate a breakpoint
Di seguito viene descritto il processo di creazione di un punto di interruzione.

## <a name="methods-in-breakpoint-creation"></a>Metodi nella creazione di punti di interruzioneMethods in breakpoint creation
 Quando viene caricato il modulo necessario per associare un punto di interruzione, il gestore di sessione di debug (SDM) chiama i metodi seguenti:When the module that is needed to bind a breakpoint is loaded, the session debug manager (SDM) calls the following methods:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** viene chiamato solo quando un utente crea un punto di interruzione dal **punti di interruzione** finestra.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Vedere anche
- [Chiamare eventi del debuggerCall debugger events](../../extensibility/debugger/calling-debugger-events.md)
