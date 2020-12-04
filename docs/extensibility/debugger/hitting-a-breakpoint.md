---
title: Raggiungimento di un punto di interruzione | Microsoft Docs
description: Questo articolo descrive il processo che si verifica quando il motore di debug raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di un'istruzione.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560850"
---
# <a name="hit-a-breakpoint"></a>Raggiungere un punto di interruzione
Nella sezione seguente viene descritto il processo quando il motore di debug (DE) raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di un'istruzione:

## <a name="troubleshoot-a-hit-breakpoint"></a>Risolvere i problemi relativi a un punto di interruzione

1. Il DE Invia un'interfaccia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) come **EVENT_SYNC_STOP**.

2. Il gestore di debug della sessione (SDM) chiama [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.

## <a name="see-also"></a>Vedere anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
