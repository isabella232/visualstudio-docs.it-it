---
title: Collegamento e scollegamento di un programma | Microsoft Docs
description: Informazioni sull'invio della sequenza corretta di metodi ed eventi con gli attributi appropriati per il fissaggio di un debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d41f9e3f88f28dbbb83e9c7e00fe8b8afd434c26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837749"
---
# <a name="attaching-and-detaching-to-a-program"></a>Collegamento e scollegamento di un programma
Per il fissaggio del debugger è necessario inviare la sequenza corretta di metodi ed eventi con gli attributi appropriati.

## <a name="sequence-of-methods-and-events"></a>Sequenza di metodi ed eventi

1. Il gestore di debug della sessione (SDM) chiama il metodo [Onconnettit](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

    In base al modello di processo del motore di debug (DE), il `IDebugProgramNodeAttach2::OnAttach` metodo restituisce uno dei metodi seguenti, che determinano cosa accade successivamente.

    Se `S_FALSE` viene restituito, il motore di debug è stato correttamente collegato al programma. In caso contrario, viene chiamato il metodo di [connessione](../../extensibility/debugger/reference/idebugengine2-attach.md) per completare il processo di connessione.

    Se `S_OK` viene restituito, il de verrà caricato nello stesso processo del SDM. SDM esegue le attività seguenti:

   1. Chiama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) per ottenere le informazioni sul motore di de.

   2. Consente di creare Co.

   3. Chiama il [Connetti](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. Il DE Invia un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) a SDM con un `EVENT_SYNC` attributo.

3. Il DE Invia un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM con un `EVENT_SYNC` attributo.

4. Il DE Invia un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM con un `EVENT_SYNC_STOP` attributo.

   Lo scollegamento da un programma è un semplice processo in due passaggi, come indicato di seguito:

5. SDM chiama [Detach](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. Il DE Invia un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Vedi anche
- [Chiamata di eventi del debugger](../../extensibility/debugger/calling-debugger-events.md)
