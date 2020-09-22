---
title: Invio di eventi di avvio dopo un avvio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839672"
---
# <a name="sending-startup-events-after-a-launch"></a>Invio degli eventi di avvio dopo un avvio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando il motore di debug (DE) viene collegato al programma, invia una serie di eventi di avvio alla sessione di debug.  
  
 Gli eventi di avvio restituiti alla sessione di debug includono quanto segue:  
  
- Evento di creazione del motore.  
  
- Evento di creazione di un programma.  
  
- Creazione di thread e eventi di caricamento del modulo.  
  
- Evento di caricamento completo, inviato quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice  
  
  > [!NOTE]
  > Quando questo evento viene continuato, le variabili globali vengono inizializzate e le routine di avvio vengono eseguite.  
  
- Possibili altri eventi di creazione del thread e di caricamento del modulo.  
  
- Un evento del punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain` . Questo evento non viene in genere inviato se il DE si connette a un programma già in esecuzione.  
  
  A livello di codice, il DE invia innanzitutto al gestore di debug della sessione (SDM) un'interfaccia [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , che rappresenta un evento di creazione del motore, seguito da un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), che rappresenta un evento di creazione del programma.  
  
  Questa operazione è in genere seguita da uno o più eventi di creazione di thread [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e da eventi di caricamento del modulo [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
  Quando il codice viene caricato e pronto per l'esecuzione, ma prima dell'esecuzione di qualsiasi codice, il DE invia l'evento SDM a [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load complete. Infine, se il programma non è ancora in esecuzione, il DE Invia un evento del punto di ingresso [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
