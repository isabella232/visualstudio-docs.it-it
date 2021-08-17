---
title: Creazione di un punto di interruzione | Microsoft Docs
description: Informazioni sulle chiamate al metodo effettuate dalla gestione del debug della sessione quando viene caricato il modulo necessario per associare un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ff6669ad1ce27582794461bd951785c3f35cde7d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080351"
---
# <a name="create-a-breakpoint"></a>Creare un punto di interruzione
Di seguito viene descritto il processo di creazione di un punto di interruzione.

## <a name="methods-in-breakpoint-creation"></a>Metodi nella creazione del punto di interruzione
 Quando viene caricato il modulo necessario per associare un punto di interruzione, la gestione del debug di sessione (SDM) chiama i metodi seguenti:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind viene chiamato** solo quando un utente crea un punto di interruzione dalla **finestra Punti di** interruzione.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Vedi anche
- [Chiamare eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
