---
title: Eliminazione di un punto di interruzione | Microsoft Docs
description: Informazioni su come la gestione del debug della sessione rimuove un punto di interruzione in sospeso e tutti i punti di interruzione associati quando viene eliminato un punto di interruzione in sospeso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: adaa20e57670148c9c7129c5c31d5de6da915515
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073344"
---
# <a name="deleting-a-breakpoint"></a>Eliminazione di un punto di interruzione
Di seguito viene descritto il processo durante l'eliminazione di un punto di interruzione in sospeso:

## <a name="deletion-process"></a>Processo di eliminazione
 Gestione debug sessione chiama il metodo [IDebugPendingBreakpoint2::D eletelete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) per rimuovere il punto di interruzione in sospeso e tutti i punti di interruzione associati.

> [!NOTE]
> Un singolo punto di interruzione associato può essere eliminato anche da una chiamata a [IDebugBoundBreakpoint2::D elete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).

## <a name="see-also"></a>Vedi anche
- [Chiamare eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
