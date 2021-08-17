---
title: Invio di eventi di avvio dopo un avvio | Microsoft Docs
description: Informazioni sulla serie di eventi di avvio che il motore di debug invia alla sessione di debug dopo che il motore di debug è collegato a un programma.
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
ms.openlocfilehash: c7449d7e4a9372482fd498c2275dc38f2d24aaad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042660"
---
# <a name="send-startup-events-after-a-launch"></a>Inviare eventi di avvio dopo un avvio
Dopo che il motore di debug (DE) è stato collegato al programma, invia una serie di eventi di avvio alla sessione di debug.

 Gli eventi di avvio inviati alla sessione di debug includono:

- Evento di creazione del motore.

- Evento di creazione del programma.

- Eventi di creazione di thread e caricamento del modulo.

- Evento di completamento del caricamento, inviato quando il codice è caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice.

  > [!NOTE]
  > Quando questo evento viene continuato, vengono inizializzate le variabili globali e vengono eseguite routine di avvio.

- Possibili altri eventi di creazione di thread e caricamento del modulo.

- Evento del punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain` . Questo evento non viene in genere inviato se de si collega a un programma già in esecuzione.

  A livello di codice, de invia prima di tutto a Gestione debug sessione un'interfaccia [IDebugEngineCreateEvent2,](../../extensibility/debugger/reference/idebugenginecreateevent2.md) che rappresenta un evento di creazione del motore, seguita da [un oggetto IDebugProgramCreateEvent2,](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)che rappresenta un evento di creazione del programma.

  Questi eventi sono in genere seguiti da uno o più eventi di creazione di thread [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e da eventi di caricamento del modulo [IDebugModuleLoadEvent2.](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)

  Quando il codice è caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice, de invia a SDM un evento di caricamento completo [IDebugLoadCompleteEvent2.](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Infine, se il programma non è già in esecuzione, DE invia un evento del punto di ingresso [IDebugEntryPointEvent2,](../../extensibility/debugger/reference/idebugentrypointevent2.md) segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.

## <a name="see-also"></a>Vedi anche
- [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
