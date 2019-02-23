---
title: L'avvio del Debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25098b58dd615cabca67e96f0d1848d1f0e8c66d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689122"
---
# <a name="launch-the-debugger"></a>Avviare il debugger
L'avvio del debugger richiede l'invio di sequenza corretta di metodi ed eventi con i relativi attributi appropriati.

## <a name="sequences-of-methods-and-events"></a>Sequenze di metodi ed eventi

1.  Gestore di sessione di debug (SDM) viene chiamato, scegliendo la **eseguire il Debug** menu e quindi selezionando **avviare**. Per altre informazioni, vedere [avviare un programma](../../extensibility/debugger/launching-a-program.md).

2.  Le chiamate SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (metodo).

3.  In base al modello di processo (DE) del motore di debug, il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce uno dei metodi seguenti, che determina ciò che accade.

     Se `S_FALSE` restituito, il motore di debug (DE) deve essere caricato in fase di macchina virtuale.

     -oppure-

     Se `S_OK` restituito, la Germania deve essere caricato in-process del messaggio SDM. Il modello SDM esegue quindi le attività seguenti:

    1.  Le chiamate [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni del motore della DE.

    2.  CO-crea il DE.

    3.  Le chiamate [collegare](../../extensibility/debugger/reference/idebugengine2-attach.md).

4.  L'invio di DE un' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.

5.  L'invio di DE un' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.

6.  L'invio di DE un' [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.

7.  L'invio di DE un' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.

8.  L'invio di DE un' [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) per il modello SDM con un `EVENT_SYNC` attributo.

## <a name="see-also"></a>Vedere anche
- [La chiamata a eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)