---
title: Associazione e distacco a un programma Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739277"
---
# <a name="attaching-and-detaching-to-a-program"></a>Associazione e disconnessione a un programma
La connessione del debugger richiede l'invio della sequenza corretta di metodi ed eventi con gli attributi appropriati.

## <a name="sequence-of-methods-and-events"></a>Sequenza di metodi ed eventi

1. Il gestore di sessione di debug (SDM) chiama il [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodo.

    In base al modello di processo `IDebugProgramNodeAttach2::OnAttach` del motore di debug (DE), il metodo restituisce uno dei metodi seguenti, che determina cosa accade successivamente.

    Se `S_FALSE` viene restituito, il motore di debug è stato collegato correttamente al programma. In caso contrario, il [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) metodo viene chiamato per completare il processo di collegamento.

    Se `S_OK` viene restituito, il DE deve essere caricato nello stesso processo del modello SDM. Il modello SDM esegue le attività seguenti:

   1. Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni sul motore del DE.

   2. Co-crea il DE.

   3. Chiamate [Allegano](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Il DE invia un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

3. Il DE invia un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

4. Il DE invia un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) per `EVENT_SYNC_STOP` il modello SDM con un attributo.

   La disconnessione da un programma è un processo semplice in due fasi, come indicato di seguito:Detaching from a program is a simple, two-step process, as follows:

5. Il file SDM chiama [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Il DE invia un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Vedere anche
- [Chiamata agli eventi del debuggerCalling debugger events](../../extensibility/debugger/calling-debugger-events.md)
