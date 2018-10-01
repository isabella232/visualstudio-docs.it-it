---
title: L'invio di eventi di avvio dopo un avvio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21b98fccac32b50e6aec643a7b69832e65d53dd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530732"
---
# <a name="sending-startup-events-after-a-launch"></a>Invio degli eventi di avvio dopo un avvio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [l'invio di avvio eventi dopo un avvio](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-startup-events-after-a-launch).  
  
Dopo che il motore di debug (DE) è collegato al programma, invia una serie di eventi di avvio nuovamente alla sessione di debug.  
  
 Gli eventi di avvio inviati nuovamente alla sessione di debug includono quanto segue:  
  
-   Un evento del motore di creazione.  
  
-   Un evento di creazione del programma.  
  
-   Eventi modulo di caricamento e la creazione del thread.  
  
-   Un evento di completamento carico, inviato quando il codice è caricato e pronto per l'esecuzione, ma prima dell'esecuzione di codice  
  
    > [!NOTE]
    >  Quando questo evento si continua, le variabili globali vengono inizializzate ed eseguire routine di avvio.  
  
-   Eventi modulo di caricamento e la creazione del thread possibili altri.  
  
-   Un evento punto di ingresso, che segnala che il programma ha raggiunto il punto di ingresso principale, ad esempio **Main** o `WinMain`. Questo evento non viene inviato in genere se la Germania si collega a un programma che è già in esecuzione.  
  
 A livello di codice la Germania invia prima un gestore di sessione di debug (SDM) un' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfaccia, che rappresenta un evento del motore di creazione, seguito da un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , che rappresenta un evento di creazione del programma.  
  
 Ciò è in genere seguita da uno o più [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) gli eventi di creazione di thread e [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventi modulo di caricamento.  
  
 Quando il codice è caricato e pronto per l'esecuzione, ma prima che venga eseguito qualsiasi codice, la Germania invia il modello SDM un' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) evento di completamento di carico. Infine, se il programma non è già in esecuzione, la Germania invia un' [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento punto di ingresso, segnalando che il programma ha raggiunto il punto di ingresso principale ed è pronto per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)

