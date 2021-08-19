---
title: Avvio del debugger | Microsoft Docs
description: Informazioni sulla sequenza di metodi ed eventi con i relativi attributi necessari per avviare il debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 72f819e9500c6a553cfe7ee73079ad439e9558d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160582"
---
# <a name="launch-the-debugger"></a>Avviare il debugger
L'avvio del debugger richiede l'invio della sequenza corretta di metodi ed eventi con gli attributi corretti.

## <a name="sequences-of-methods-and-events"></a>Sequenze di metodi ed eventi

1. La gestione del debug di sessione (SDM) viene chiamata scegliendo il menu **Debug** e quindi **scegliendo Avvia**. Per altre informazioni, vedere [Avviare un programma](../../extensibility/debugger/launching-a-program.md).

2. SDM chiama [il metodo OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

3. In base al modello di processo del motore di debug, il metodo restituisce uno dei metodi seguenti, che determina `IDebugProgramNodeAttach2::OnAttach` cosa accade successivamente.

     Se `S_FALSE` restituisce , il motore di debug (DE) deve essere caricato nel processo della macchina virtuale.

     -oppure-

     Se `S_OK` restituisce , il de deve essere caricato in-process di SDM. SDM esegue quindi le attività seguenti:

    1. Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni sul motore del de.

    2. Crea in modo co-creato il de.

    3. Chiama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. Il de invia [un oggetto IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

5. Il de invia [un oggetto IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

6. Il de invia un [oggetto IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

7. Il de invia [un oggetto IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un `EVENT_SYNC` attributo .

8. Il de invia [un IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a SDM con un `EVENT_SYNC` attributo .

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
- [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)
