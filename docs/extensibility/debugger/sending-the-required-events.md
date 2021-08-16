---
title: Invio degli eventi necessari | Microsoft Docs
description: Informazioni sugli eventi ordinati necessari quando si crea un motore di debug e lo si collega a un programma Visual Studio debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5080564527d2037c4ea376bc11c5df5a397c623616b6c08e62ab79e684256548
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448494"
---
# <a name="send-the-required-events"></a>Inviare gli eventi necessari
Utilizzare questa procedura per inviare gli eventi necessari.

## <a name="process-for-sending-required-events"></a>Processo per l'invio di eventi necessari
 Quando si crea un motore di debug (DE) e lo si collega a un programma, sono necessari gli eventi seguenti:

1. Inviare un oggetto evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al gestore di debug sessione (SDM) quando il de viene inizializzato per il debug di uno o più programmi in un processo.

2. Quando il programma a cui eseguire il debug è collegato, inviare un oggetto evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a SDM. Questo evento può essere un evento di arresto, a seconda della progettazione del motore.

3. Se il programma è collegato a all'avvio del processo, inviare un oggetto evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a SDM per notificare all'IDE il nuovo thread. Questo evento può essere un evento di arresto, a seconda della progettazione del motore.

4. Inviare un oggetto evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) a SDM al termine del caricamento del programma in fase di debug o al completamento della connessione al programma. Questo evento deve essere un evento di arresto.

5. Se viene avviata l'applicazione di cui eseguire il debug, inviare un oggetto evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) a SDM quando sta per essere eseguita la prima istruzione di codice nell'architettura di run-time. Questo evento è sempre un evento di arresto. Quando si esegue un'istruzione alla sessione di debug, l'IDE si arresta in questo evento.

> [!NOTE]
> Molti linguaggi usano inizializzatori globali o funzioni precompilate esterne (dalla libreria CRT o _Main) all'inizio del codice. Se il linguaggio del programma di cui si esegue il debug contiene uno di questi tipi di elementi prima del punto di ingresso iniziale, questo codice viene eseguito e l'evento del punto di ingresso viene inviato quando viene raggiunto il punto di ingresso dell'utente, ad esempio **main** o `WinMain` .

## <a name="see-also"></a>Vedi anche
- [Abilitazione del debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
