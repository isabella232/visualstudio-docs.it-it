---
title: Collegamento e scollegamento a un programma | Microsoft Docs
description: Informazioni sull'invio della sequenza corretta di metodi ed eventi con gli attributi corretti per il collegamento di un debugger.
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
ms.openlocfilehash: 1c4fa3240e5d2226b43e656bf2007dad9e21219a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051092"
---
# <a name="attaching-and-detaching-to-a-program"></a>Collegamento e disconnessione a un programma
Per collegare il debugger è necessario inviare la sequenza corretta di metodi ed eventi con gli attributi corretti.

## <a name="sequence-of-methods-and-events"></a>Sequenza di metodi ed eventi

1. Il gestore di debug di sessione (SDM) chiama il [metodo OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    In base al modello di processo del motore di debug, il metodo restituisce uno dei metodi seguenti, che determina `IDebugProgramNodeAttach2::OnAttach` cosa accade successivamente.

    Se `S_FALSE` viene restituito , il motore di debug è stato collegato correttamente al programma. In caso contrario, [viene chiamato](../../extensibility/debugger/reference/idebugengine2-attach.md) il metodo Attach per completare il processo di connessione.

    Se `S_OK` viene restituito , il de deve essere caricato nello stesso processo di SDM. SDM esegue le attività seguenti:

   1. Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni sul motore del de.

   2. Crea in modo co-creato il de.

   3. Chiama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Il de invia [un oggetto IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

3. Il de invia [un oggetto IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un `EVENT_SYNC` attributo .

4. Il de invia [un oggetto IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un `EVENT_SYNC_STOP` attributo .

   La disconnessione da un programma è un processo semplice in due passaggi, come indicato di seguito:

5. SDM chiama [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Il de invia un [IDebugProgramDestroyEvent2.](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
