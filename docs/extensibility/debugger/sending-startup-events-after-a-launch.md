---
title: Invio di eventi di avvio dopo un avvio | Microsoft Docs
description: Informazioni sulle serie di eventi di avvio inviati dal motore di debug alla sessione di debug dopo che il motore di debug è associato a un programma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 227d863df1e3318d2df6be6a24aaf05b5033e92d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070400"
---
# <a name="send-startup-events-after-a-launch"></a>Invia eventi di avvio dopo un avvio
Quando il motore di debug (DE) viene collegato al programma, invia una serie di eventi di avvio alla sessione di debug.

 Gli eventi di avvio restituiti alla sessione di debug includono:

- Evento di creazione del motore.

- Evento di creazione di un programma.

- Creazione di thread e eventi di caricamento del modulo.

- Evento di caricamento completo, inviato quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione del codice.

  > [!NOTE]
  > Quando questo evento viene continuato, le variabili globali vengono inizializzate e le routine di avvio vengono eseguite.

- Possibili altri eventi di creazione del thread e di caricamento del modulo.

- Un evento del punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain` . Questo evento non viene in genere inviato se il DE si connette a un programma già in esecuzione.

  A livello di codice, il DE invia innanzitutto al gestore di debug della sessione (SDM) un'interfaccia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , che rappresenta un evento di creazione del motore, seguito da un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), che rappresenta un evento di creazione del programma.

  Questi eventi sono in genere seguiti da uno o più eventi di creazione di thread [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e da eventi di caricamento del modulo [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .

  Quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice, il DE invia l'evento SDM a [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load complete. Infine, se il programma non è già in esecuzione, il DE Invia un evento del punto di ingresso [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.

## <a name="see-also"></a>Vedi anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
