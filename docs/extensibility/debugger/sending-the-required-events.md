---
title: Invio degli eventi richiesti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713000"
---
# <a name="send-the-required-events"></a>Inviare gli eventi richiesti
Utilizzare questa procedura per inviare gli eventi richiesti.

## <a name="process-for-sending-required-events"></a>Processo per l'invio degli eventi richiesti
 Gli eventi seguenti sono necessari, in questo ordine, quando si crea un motore di debug (DE) e lo si collega a un programma:The following events are required, in this order, when creating a debug engine (DE) and attaching it to a program:

1. Inviare un oggetto evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al gestore di sessione di debug (SDM) quando il DE viene inizializzato per il debug di uno o più programmi in un processo.

2. Quando il programma di cui eseguire il debug è collegato, inviare un oggetto evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al modello SDM. Questo evento può essere un evento di arresto, a seconda della progettazione del motore.

3. Se il programma è collegato a quando viene avviato il processo, inviare un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) oggetto evento per il modello SDM per notificare l'IDE del nuovo thread. Questo evento può essere un evento di arresto, a seconda della progettazione del motore.

4. Inviare un oggetto evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al modello SDM al termine del caricamento del programma sottoposto a debug o al termine della connessione al programma. Questo evento deve essere un evento di arresto.

5. Se l'applicazione di cui eseguire il debug viene avviata, inviare un oggetto evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al modello SDM quando sta per essere eseguita la prima istruzione di codice nell'architettura di runtime. Questo evento è sempre un evento di arresto. Quando si esegue un'istruzione nella sessione di debug, l'IDE si arresta su questo evento.

> [!NOTE]
> Molti linguaggi utilizzano inizializzatori globali o funzioni precompilate esterne (dalla libreria CRT o _Main) all'inizio del codice. Se il linguaggio del programma di cui si sta eseguendo il debug contiene uno di questi tipi di elementi prima **main** del `WinMain`punto di ingresso iniziale, questo codice viene eseguito e l'evento del punto di ingresso viene inviato quando viene raggiunto il punto di ingresso dell'utente, ad esempio main o ,

## <a name="see-also"></a>Vedere anche
- [Abilitazione del debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
