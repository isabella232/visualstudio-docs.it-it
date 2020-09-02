---
title: Contesto del codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197367"
---
# <a name="code-context"></a>Contesto del codice
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug, un **contesto di codice**:  
  
- Fornisce un'astrazione di una posizione nel codice come noto al motore di debug (DE). Per la maggior parte delle architetture di runtime oggi, un contesto di codice può essere considerato come un indirizzo nel flusso di istruzioni di un programma. Per le lingue non tradizionali, in cui il codice non può essere rappresentato dalle istruzioni, un contesto di codice può essere rappresentato da altri mezzi.  
  
- Descrive la posizione corrente nel flusso di esecuzione del programma di cui è in corso il debug.  
  
- Esiste solo quando un programma è stato interrotto in corrispondenza di un punto di interruzione.  
  
- Dispone di un contesto del documento associato.  
  
- Viene implementato da un'interfaccia [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Contesto del documento](../../extensibility/debugger/document-context.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
