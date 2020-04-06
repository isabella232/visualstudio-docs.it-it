---
title: Invio di eventi di avvio dopo un avvio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713009"
---
# <a name="send-startup-events-after-a-launch"></a>Inviare eventi di avvio dopo un avvio
Una volta che il motore di debug (DE) è collegato al programma, invia una serie di eventi di avvio alla sessione di debug.

 Gli eventi di avvio inviati alla sessione di debug includono:Startup events sent back to the debug session include:

- Un evento di creazione del motore.

- Un evento di creazione del programma.

- Eventi di creazione dei thread e caricamento del modulo.

- Un evento load complete, inviato quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice.

  > [!NOTE]
  > Quando questo evento continua, vengono inizializzate le variabili globali e vengono eseguite le routine di avvio.

- Possibili altri eventi di creazione del thread e di caricamento del modulo.

- Un evento del punto di ingresso, che segnala che **Main** il `WinMain`programma ha raggiunto il punto di ingresso principale, ad esempio Main o . Questo evento non viene in genere inviato se il DE si connette a un programma che è già in esecuzione.

  A livello di codice, il DE invia innanzitutto il gestore di debug della sessione (SDM) un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia, che rappresenta un evento di creazione del motore, seguito da un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), che rappresenta un evento di creazione del programma.

  Questi eventi sono in genere seguiti da uno o più eventi di creazione del thread [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e eventi di caricamento del modulo [IDebugModuleLoadEvent2.These](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) events are typically followed by one or more IDebugThreadCreateEvent2 thread creation events and IDebugModuleLoadEvent2 module load events.

  Quando il codice viene caricato e pronto per l'esecuzione, ma prima che venga eseguito qualsiasi codice, il DE invia il Modello SDM un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) evento di completamento. Infine, se il programma non è già in esecuzione, il DE invia un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento del punto di ingresso, segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.

## <a name="see-also"></a>Vedere anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
