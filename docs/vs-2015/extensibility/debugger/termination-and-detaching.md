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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968971"
---
# <a name="termination-and-detaching"></a>Terminazione e scollegamento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Di seguito vengono descritti la terminazione normale.  
  
## <a name="discussion"></a>Discussione  
 Dopo il [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oppure [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfaccia continua, se non esistono punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug, il programma sottoposto a debug verrà eseguito fino al completamento. Si tratta di chiusura normale.  
  
 È necessario inviare un' [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) implementare terminazione normale. Ciò richiede l'implementazione di [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)
