---
title: Raggiungere un punto di interruzione | Microsoft Docs
description: Questo articolo descrive il processo che viene eseguito quando il motore di debug raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di istruzioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 04c9c5a3526b1e1c42034d606d2a2cc588a748533e65a99a2907328be16ac8e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361184"
---
# <a name="hit-a-breakpoint"></a>Raggiungere un punto di interruzione
La sezione seguente descrive il processo quando il motore di debug raggiunge un punto di interruzione durante l'esecuzione o l'esecuzione di istruzioni:

## <a name="troubleshoot-a-hit-breakpoint"></a>Risolvere i problemi relativi a un punto di interruzione raggiunto

1. Il de invia [un'interfaccia IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) **come EVENT_SYNC_STOP**.

2. Gestione debug sessione chiama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere il punto di interruzione raggiunto.

## <a name="see-also"></a>Vedi anche
- [Chiamare eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
