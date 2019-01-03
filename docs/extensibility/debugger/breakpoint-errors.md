---
title: Errori di punto di interruzione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a51f418483d58a5fce33fed0e49b695043c16cde
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857156"
---
# <a name="breakpoint-errors"></a>Errori di punto di interruzione
Di seguito viene descritto il processo quando un punto di interruzione tenta di eseguire l'associazione al codice ma non riesce.  
  
## <a name="troubleshoot-a-breakpoint-error"></a>Risolvere un errore di punto di interruzione  
  
1.  Il motore di debug (DE) invia un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al gestore di sessione di debug (SDM).  
  
2.  Le chiamate SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) per ottenere il punto di interruzione di errore.  
  
3.  Le chiamate SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) per ottenere il punto di interruzione in sospeso da cui ha avuto origine il punto di interruzione di errore.  
  
4.  Le chiamate SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) per ottenere il motivo per cui il punto di interruzione di errore non è stato possibile associare.  
  
## <a name="see-also"></a>Vedere anche  
 [La chiamata a eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)