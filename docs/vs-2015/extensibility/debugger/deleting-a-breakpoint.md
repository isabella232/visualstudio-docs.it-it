---
title: Eliminazione di un punto di interruzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839732"
---
# <a name="deleting-a-breakpoint"></a>Eliminazione di un punto di interruzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritto il processo di eliminazione di un punto di interruzione in sospeso:  
  
## <a name="deletion-process"></a>Processo di eliminazione  
 Il gestore di debug della sessione (SDM) chiama il metodo [IDebugPendingBreakpoint2::D Elimina](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) per rimuovere il punto di interruzione in sospeso e tutti i punti di interruzione associati.  
  
> [!NOTE]
> Un punto di interruzione associato singolo può essere eliminato anche da una chiamata a [IDebugBoundBreakpoint2::D Elimina](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
