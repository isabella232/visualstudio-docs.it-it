---
title: Terminazione di un programma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3bc26486db7cdc5f8a29477b4380041b506c4e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772911"
---
# <a name="terminating-a-program"></a>Terminazione di un programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito è una descrizione della chiusura di un singolo programma con un solo thread.  
  
## <a name="termination-process"></a>Processo di terminazione  
  
1. L'invio di DE un' [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un valore valido [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. L'invio di DE un' [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un valore valido [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   L'IDE passa alla modalità progettazione. Il motore di debug o di un ambiente di runtime chiama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)

