---
title: Terminazione e scollegamento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176666"
---
# <a name="termination-and-detaching"></a>Terminazione e scollegamento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito viene descritta la chiusura normale.  
  
## <a name="discussion"></a>Discussione  
 Quando l'interfaccia [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) continua, se non sono presenti punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione di cui eseguire il debug, il programma di cui è in corso il debug verrà eseguito fino al completamento. Si tratta di una chiusura normale.  
  
 Per implementare la terminazione normale è necessario inviare un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . A tale scopo, è necessario implementare il metodo [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
