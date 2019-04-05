---
title: Collegamento e scollegamento da un programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98b1f0f97aa33c56df7a512389daf1801157e693
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955955"
---
# <a name="attaching-and-detaching-to-a-program"></a>Collegamento e scollegamento da un programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per collegare il debugger richiede l'invio di sequenza corretta di metodi ed eventi con gli attributi appropriati.  
  
## <a name="sequence-of-methods-and-events"></a>Sequenza di metodi ed eventi  
  
1. Gestore di sessione di debug (SDM) chiama il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (metodo).  
  
    In base al modello di processo (DE) del motore di debug, il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce uno dei metodi seguenti, che determina ciò che accade.  
  
    Se `S_FALSE` viene restituito, il motore di debug è stato collegato correttamente al programma. In caso contrario, il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato per completare il processo di collegamento.  
  
    Se `S_OK` viene restituito, deve essere caricato nello stesso processo come il modello SDM la Germania. Il modello SDM esegue le attività seguenti:  
  
   1.  Le chiamate [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni del motore della DE.  
  
   2.  CO-crea il DE.  
  
   3.  Le chiamate [collegare](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2. L'invio di DE un' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.  
  
3. L'invio di DE un' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.  
  
4. L'invio di DE un' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) per il modello SDM con un `EVENT_SYNC_STOP` attributo.  
  
   La disconnessione da un programma è un semplice processo in due passaggi, come indicato di seguito:  
  
5. Le chiamate SDM [Scollega](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
6. L'invio di DE un' [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Chiamata degli eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
