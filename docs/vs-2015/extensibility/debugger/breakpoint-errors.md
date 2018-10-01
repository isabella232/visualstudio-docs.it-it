---
title: Errori di punto di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 656f96a344e3d527407cd5a91b0a5910e1e6005c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525903"
---
# <a name="breakpoint-errors"></a>Errori dei punti di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [punto di interruzione errori](https://docs.microsoft.com/visualstudio/extensibility/debugger/breakpoint-errors).  
  
Di seguito viene descritto il processo quando un punto di interruzione tenta di eseguire l'associazione al codice ma ha esito negativo:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Risoluzione dei problemi di un errore di punto di interruzione  
  
1.  Il motore di debug (DE) invia un [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) al gestore di sessione di debug (SDM).  
  
2.  Le chiamate SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) per ottenere il punto di interruzione di errore.  
  
3.  Le chiamate SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) per ottenere il punto di interruzione in sospeso da cui ha avuto origine il punto di interruzione di errore.  
  
4.  Le chiamate SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) per ottenere il motivo per cui il punto di interruzione di errore non è stato possibile associare.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)

