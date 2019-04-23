---
title: Invio degli eventi richiesti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcff0d559894e8d4ba322e4e8ebab71000a3809e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083556"
---
# <a name="send-the-required-events"></a>Inviare gli eventi richiesti
Utilizzare questa procedura per l'invio degli eventi necessari.

## <a name="process-for-sending-required-events"></a>Processo per l'invio di eventi richiesti
 Gli eventi seguenti sono necessari, in quest'ordine, la creazione di un debug del motore (DE) e collegarlo a un programma:

1. Invio di un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto dell'evento al gestore di sessione di debug (SDM) quando viene inizializzata la Germania per il debug di uno o più programmi in un processo.

2. Quando il programma da sottoporre a debug è collegato a, inviare un' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) oggetto dell'evento per il modello SDM. Questo evento può essere un evento di arresto, a seconda della progettazione di motore.

3. Se il programma viene collegato quando viene avviato il processo, inviare un' [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) oggetto dell'evento per il modello SDM per notificare l'IDE del nuovo thread. Questo evento può essere un evento di arresto, a seconda della progettazione di motore.

4. Invio di un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oggetto dell'evento per il modello SDM quando il programma sottoposto a debug è terminato il caricamento o quando viene completata la connessione al programma. Questo evento deve essere un evento di arresto.

5. Se viene avviata l'applicazione da sottoporre a debug, inviare un' [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) oggetto dell'evento per il modello SDM quando la prima istruzione del codice nell'architettura di runtime deve essere eseguito. Si tratta sempre un evento di arresto. Quando si esegue l'istruzione nella sessione di debug, l'IDE si interrompe in questo evento.

> [!NOTE]
>  Molti linguaggi di usano gli inizializzatori globali o funzioni precompilate esterne (della libreria CRT o Main) all'inizio del codice. Se la lingua del programma di debug contiene uno di questi tipi di elementi che precedono il punto di ingresso iniziale, questo codice viene eseguito e viene inviato l'evento punto di ingresso quando utenti del punto di ingresso, ad esempio **principale** o `WinMain`, è raggiunto.

## <a name="see-also"></a>Vedere anche
- [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)