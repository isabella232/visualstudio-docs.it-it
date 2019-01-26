---
title: Terminazione e scollegamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efaeb409d49c31e47f66bb5d593d1da6a3d97919
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971559"
---
# <a name="termination-and-detaching"></a>Terminazione e scollegamento
La sezione seguente descrive terminazione normale.  
  
## <a name="discussion"></a>Discussione  
 Dopo il [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oppure [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interfaccia continua, se non esistono punti di interruzione, eccezioni, errori di run-time o cicli infiniti nell'applicazione da sottoporre a debug, il programma in fase di debug viene eseguito fino al completamento. Questo processo è terminazione normale.  
  
 È necessario inviare un' [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) implementare terminazione normale. Terminazione normale richiede l'esecuzione di [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (metodo).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)