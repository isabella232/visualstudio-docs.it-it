---
title: Invio di eventi di avvio dopo un avvio | Microsoft Docs
description: Informazioni sulla serie di eventi di avvio inviati dal motore di debug alla sessione di debug dopo che il motore di debug è collegato a un programma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eb5d382d54d8263cfe0e72f2c828453b8c29aba097973e7c32f1640cc1d2d4a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414948"
---
# <a name="send-startup-events-after-a-launch"></a>Inviare eventi di avvio dopo un avvio
Dopo aver collegato il motore di debug (DE) al programma, invia una serie di eventi di avvio alla sessione di debug.

 Gli eventi di avvio inviati alla sessione di debug includono:

- Evento di creazione del motore.

- Evento di creazione del programma.

- Eventi di creazione di thread e caricamento del modulo.

- Evento di caricamento completato, inviato quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice.

  > [!NOTE]
  > Quando questo evento viene continuato, le variabili globali vengono inizializzate e vengono eseguite routine di avvio.

- Possibili altri eventi di creazione di thread e caricamento del modulo.

- Evento del punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain` . Questo evento non viene in genere inviato se de si collega a un programma già in esecuzione.

  A livello di codice, il DE invia prima di tutto al gestore di debug della sessione (SDM) [un'interfaccia IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) che rappresenta un evento di creazione del motore, seguito da [un oggetto IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), che rappresenta un evento di creazione del programma.

  Questi eventi sono in genere seguiti da uno o più eventi di creazione di thread [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e da eventi di caricamento del modulo [IDebugModuleLoadEvent2.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice, il DE invia a SDM un evento di caricamento [IDebugLoadCompleteEvent2.](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Infine, se il programma non è già in esecuzione, il DE invia un evento del punto di ingresso [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.

## <a name="see-also"></a>Vedi anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
