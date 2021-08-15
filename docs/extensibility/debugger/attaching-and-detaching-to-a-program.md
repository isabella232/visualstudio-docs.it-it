---
title: Collegamento e disconnessione a un programma | Microsoft Docs
description: Informazioni sull'invio della sequenza corretta di metodi ed eventi con gli attributi corretti per collegare un debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 678b2a3582eef3b803a838728a43a7e1444de064b3e29778fd5f077ab7c386f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121324158"
---
# <a name="attaching-and-detaching-to-a-program"></a>Collegamento e disconnessione a un programma
Il collegamento del debugger richiede l'invio della sequenza corretta di metodi ed eventi con gli attributi corretti.

## <a name="sequence-of-methods-and-events"></a>Sequenza di metodi ed eventi

1. La gestione del debug di sessione (SDM) chiama il [metodo OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    In base al modello di processo del motore di debug, il metodo restituisce uno dei metodi seguenti, che determina `IDebugProgramNodeAttach2::OnAttach` cosa accade successivamente.

    Se `S_FALSE` viene restituito , il motore di debug è stato collegato correttamente al programma. In caso contrario, [viene](../../extensibility/debugger/reference/idebugengine2-attach.md) chiamato il metodo Attach per completare il processo di connessione.

    Se `S_OK` viene restituito , de deve essere caricato nello stesso processo di SDM. SDM esegue le attività seguenti:

   1. Chiama [GetEngineInfo per](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) ottenere le informazioni sul motore di DE.

   2. Crea il de-de co-creato.

   3. Chiama [Attach.](../../extensibility/debugger/reference/idebugengine2-attach.md)

2. DE invia un [oggetto IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

3. DE invia un [oggetto IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

4. DE invia un [oggetto IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un `EVENT_SYNC_STOP` attributo .

   La disconnessione da un programma è un processo semplice in due passaggi, come indicato di seguito:

5. SDM chiama [Detach.](../../extensibility/debugger/reference/idebugprogram2-detach.md)

6. DE invia un [oggetto IDebugProgramDestroyEvent2.](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
