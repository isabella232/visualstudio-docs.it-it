---
title: Creazione di un punto di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04eefdca7459f95da3ddef0430a59f9af52e581e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203901"
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