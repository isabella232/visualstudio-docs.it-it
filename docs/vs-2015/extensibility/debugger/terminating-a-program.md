---
title: Terminazione di un programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421863"
---
# <a name="terminating-a-program"></a>Terminazione di un programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito è riportata una descrizione della chiusura di un singolo programma con un solo thread.  
  
## <a name="termination-process"></a>Processo di terminazione  
  
1. Il DE Invia un [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) con un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)valido.  
  
2. Il DE Invia un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) con un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)valido.  
  
   L'IDE passa alla modalità progettazione. Il motore di debug o l'ambiente di run-time chiama [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) per rimuovere il programma dalla porta.  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
