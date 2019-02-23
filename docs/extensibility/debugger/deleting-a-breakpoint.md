---
title: L'eliminazione di un punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22cada0aaf77edd241992229c2bd6733be3ccc81
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711163"
---
# <a name="deleting-a-breakpoint"></a>L'eliminazione di un punto di interruzione
Di seguito viene descritto il processo quando si elimina un punto di interruzione in sospeso:

## <a name="deletion-process"></a>Processo di eliminazione
 Gestore di sessione di debug (SDM) chiama il [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodo per rimuovere il punto di interruzione in sospeso e i punti di interruzione con tutti i binding associati da quest'ultimo.

> [!NOTE]
>  È inoltre possibile rimuovere un singolo punto di interruzione associato da una chiamata a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Vedere anche
- [Chiamare gli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)