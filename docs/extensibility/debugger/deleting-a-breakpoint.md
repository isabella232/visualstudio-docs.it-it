---
title: Eliminazione di un punto di interruzione | Microsoft Docs
description: Informazioni su come gestione debug sessione rimuove un punto di interruzione in sospeso e tutti i punti di interruzione associati quando viene eliminato un punto di interruzione in sospeso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915557"
---
# <a name="deleting-a-breakpoint"></a>Eliminazione di un punto di interruzione
Di seguito viene descritto il processo di eliminazione di un punto di interruzione in sospeso:

## <a name="deletion-process"></a>Processo di eliminazione
 Il gestore di debug della sessione (SDM) chiama il metodo [IDebugPendingBreakpoint2::D Elimina](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) per rimuovere il punto di interruzione in sospeso e tutti i punti di interruzione associati.

> [!NOTE]
> Un punto di interruzione associato singolo può essere eliminato anche da una chiamata a [IDebugBoundBreakpoint2::D Elimina](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Vedi anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
