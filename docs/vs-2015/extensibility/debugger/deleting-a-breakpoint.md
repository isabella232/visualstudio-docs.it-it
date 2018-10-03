---
title: L'eliminazione di un punto di interruzione | Microsoft Docs
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
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18b88cc55a4c641e56c062356a9f74c2224835a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529144"
---
# <a name="deleting-a-breakpoint"></a>Eliminazione di un punto di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [l'eliminazione di un punto di interruzione](https://docs.microsoft.com/visualstudio/extensibility/debugger/deleting-a-breakpoint).  
  
Di seguito viene descritto il processo quando si elimina un punto di interruzione in sospeso:  
  
## <a name="deletion-process"></a>Processo di eliminazione  
 Gestore di sessione di debug (SDM) chiama il [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) metodo per rimuovere il punto di interruzione in sospeso e i punti di interruzione con tutti i binding associati da quest'ultimo.  
  
> [!NOTE]
>  È inoltre possibile rimuovere un singolo punto di interruzione associato da una chiamata a [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)

