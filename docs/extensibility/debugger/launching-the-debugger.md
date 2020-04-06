---
title: Avvio del debugger Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738451"
---
# <a name="launch-the-debugger"></a>Avviare il debugger
L'avvio del debugger richiede l'invio della sequenza corretta di metodi ed eventi con gli attributi appropriati.

## <a name="sequences-of-methods-and-events"></a>Sequenze di metodi ed eventi

1. Il gestore di debug della sessione (SDM) viene chiamato scegliendo il menu **Debug** e quindi **Facendo clic su Avvia**. Per ulteriori informazioni, consultate [Avviare un programma.](../../extensibility/debugger/launching-a-program.md)

2. Il metodo SDM chiama il metodo [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

3. In base al modello di processo `IDebugProgramNodeAttach2::OnAttach` del motore di debug (DE), il metodo restituisce uno dei metodi seguenti, che determina cosa accade successivamente.

     Se `S_FALSE` restituisce una restituzione, il motore di debug (DE) deve essere caricato nel processo della macchina virtuale.

     -oppure-

     Se `S_OK` restituisce, il DE deve essere caricato in-process del modello SDM. Il modello SDM esegue quindi le attività seguenti:

    1. Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni sul motore del DE.

    2. Co-crea il DE.

    3. Chiamate [Allegano](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Il DE invia un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

5. Il DE invia un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

6. Il DE invia un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

7. Il DE invia un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

8. Il DE invia un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) per `EVENT_SYNC` il modello SDM con un attributo.

## <a name="see-also"></a>Vedere anche
- [Chiamata agli eventi del debuggerCalling debugger events](../../extensibility/debugger/calling-debugger-events.md)
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
