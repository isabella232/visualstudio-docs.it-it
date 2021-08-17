---
title: Errori dei punti di interruzione | Microsoft Docs
description: Informazioni sul processo quando un punto di interruzione tenta di eseguire l'associazione al codice ma non riesce e su come risolvere gli errori dei punti di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 592441e057e5b726f6fb474bf4dae66365203d73a64eb569b6e785ac1d1f2d48
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403346"
---
# <a name="breakpoint-errors"></a>Errori dei punti di interruzione
Di seguito viene descritto il processo quando un punto di interruzione tenta di eseguire l'associazione al codice ma non riesce.

## <a name="troubleshoot-a-breakpoint-error"></a>Risolvere l'errore di un punto di interruzione

1. Il motore di debug (DE) invia [un IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al gestore di debug sessione (SDM).

2. SDM chiama [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2** ) per ottenere il punto `ppErrorBP` di interruzione dell'errore.

3. SDM chiama [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) per ottenere il punto di interruzione in sospeso da cui ha avuto origine il punto di interruzione dell'errore.

4. SDM chiama [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) per ottenere il motivo per cui non è stato possibile associare il punto di interruzione dell'errore.

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
