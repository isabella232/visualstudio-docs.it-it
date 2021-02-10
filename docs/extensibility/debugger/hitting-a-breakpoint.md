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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 808bf95631bb4106d071c29d7af233d071ef5229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947723"
---
# <a name="hit-a-breakpoint"></a>Raggiungere un punto di interruzione
Nella sezione seguente viene descritto il processo quando il motore di debug (DE) raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di un'istruzione:

## <a name="troubleshoot-a-hit-breakpoint"></a>Risolvere i problemi relativi a un punto di interruzione

1. Il DE Invia un'interfaccia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) come **EVENT_SYNC_STOP**.

2. Il gestore di debug della sessione (SDM) chiama [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.

## <a name="see-also"></a>Vedi anche
- [Chiama eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
