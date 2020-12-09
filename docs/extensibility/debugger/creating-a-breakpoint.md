---
title: Creazione di un punto di interruzione | Microsoft Docs
description: Informazioni sulle chiamate ai metodi eseguite dal gestore di debug della sessione quando viene caricato il modulo necessario per associare un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba192a0cda2e63453984d3de7d6007744cc401b7
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914228"
---
# <a name="create-a-breakpoint"></a>Creazione di un punto di interruzione
Di seguito viene descritto il processo di creazione di un punto di interruzione.

## <a name="methods-in-breakpoint-creation"></a>Metodi nella creazione di punti di interruzione
 Quando viene caricato il modulo necessario per associare un punto di interruzione, il gestore di debug della sessione (SDM) chiama i metodi seguenti:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** viene chiamato solo quando un utente crea un punto di interruzione dalla finestra punti di **interruzione** .

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Vedi anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
