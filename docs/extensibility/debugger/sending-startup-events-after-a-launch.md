---
title: L'invio di eventi di avvio dopo un avvio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: caa9f615c6ed6f314695b195a6095d238382a4c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967500"
---
# <a name="send-startup-events-after-a-launch"></a>Inviare gli eventi di avvio dopo un avvio
Dopo che il motore di debug (DE) è collegato al programma, invia una serie di eventi di avvio nuovamente alla sessione di debug.  
  
 Gli eventi di avvio inviati nuovamente alla sessione di debug includono:  
  
- Un evento del motore di creazione.  
  
- Un evento di creazione del programma.  
  
- Eventi modulo di caricamento e la creazione del thread.  
  
- Un carico evento di completamento, inviato quando il codice è caricato e pronto per l'esecuzione, ma prima che venga eseguito qualsiasi codice. 
  
  > [!NOTE]
  >  Quando questo evento si continua, le variabili globali vengono inizializzate ed eseguire routine di avvio.  
  
- Eventi modulo di caricamento e la creazione del thread possibili altri.  
  
- Un evento punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain`. Questo evento non è in genere inviato se la Germania si collega a un programma che è già in esecuzione.  
  
  A livello di codice la Germania invia prima un gestore di sessione di debug (SDM) un' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia, che rappresenta un evento del motore di creazione, seguito da un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , che rappresenta un evento di creazione del programma.  
  
  Questi eventi vengono in genere seguiti da uno o più [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) gli eventi di creazione di thread e [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventi modulo di caricamento.  
  
  Quando il codice è caricato e pronto per l'esecuzione, ma prima che venga eseguito qualsiasi codice, la Germania invia il modello SDM un' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) evento di completamento di carico. Infine, se il programma non è già in esecuzione, la Germania invia un' [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento punto di ingresso, segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)