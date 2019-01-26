---
title: Creazione di un punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16fc85090b59909add7ae228a795c6396ca61a3c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967232"
---
# <a name="create-a-breakpoint"></a>Creare un punto di interruzione
Di seguito viene descritto il processo di creazione di un punto di interruzione.  
  
## <a name="methods-in-breakpoint-creation"></a>Metodi di creazione punto di interruzione  
 Quando viene caricato il modulo che è necessario associare un punto di interruzione, gestione del debug (SDM) la sessione chiama i metodi seguenti:  
  
1.  [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** viene chiamato solo quando un utente esegue un punto di interruzione dal **punti di interruzione** finestra.  
  
4.  [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamare gli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)