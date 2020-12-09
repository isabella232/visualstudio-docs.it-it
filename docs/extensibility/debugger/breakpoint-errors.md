---
title: Errori del punto di interruzione | Microsoft Docs
description: Informazioni sul processo quando un punto di interruzione tenta di eseguire l'associazione al codice, ma ha esito negativo e come risolvere gli errori del punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a5003ce8abe79fcba9f9604047d2265810fda2
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914491"
---
# <a name="breakpoint-errors"></a>Errori del punto di interruzione
Di seguito viene descritto il processo quando un punto di interruzione tenta di eseguire l'associazione al codice ma ha esito negativo.

## <a name="troubleshoot-a-breakpoint-error"></a>Risolvere un errore del punto di interruzione

1. Il motore di debug (DE) Invia un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al gestore di debug della sessione (SDM).

2. SDM chiama [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) per ottenere il punto di interruzione dell'errore.

3. SDM chiama [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) per ottenere il punto di interruzione in sospeso da cui ha avuto origine il punto di interruzione dell'errore.

4. SDM chiama [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) per ottenere il motivo per cui non è stato possibile associare il punto di interruzione dell'errore.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
