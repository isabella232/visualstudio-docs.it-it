---
title: Tipi di evento supportati | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f671e8d0128bee2c52dc1191b33edb889c92d2e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839928"
---
# <a name="supported-event-types"></a>Tipi di evento supportati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il debug di Visual Studio supporta attualmente i tipi di evento seguenti:  
  
- Eventi asincroni  
  
   Notificare alla gestione del debug della sessione (SDM) e all'IDE che lo stato dell'applicazione in fase di debug sta cambiando. Questi eventi vengono elaborati a piacimento di SDM e dell'IDE. Non viene inviata alcuna risposta al motore di debug (DE) dopo l'elaborazione dell'evento. Le interfacce [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sono esempi di eventi asincroni.  
  
- Eventi sincroni  
  
   Notificare a SDM e IDE che lo stato dell'applicazione in fase di debug sta cambiando. L'unica differenza tra questi eventi ed eventi asincroni è che una risposta viene inviata tramite il metodo [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .  
  
   L'invio di un evento sincrono è utile se è necessario che il DE continui l'elaborazione dopo che l'IDE riceve ed elabora l'evento.  
  
- Eventi di arresto sincrono o arresto di eventi  
  
   Notificare a SDM e all'IDE che l'applicazione di cui è in corso il debug ha interrotto l'esecuzione del codice. Quando si invia un evento di arresto per mezzo dell' [evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md)del metodo, il parametro [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) è obbligatorio. L'arresto degli eventi continua con una chiamata a uno dei metodi seguenti:  
  
  - [Eseguire](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continua](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di arresto degli eventi.  
  
  > [!NOTE]
  > Gli eventi di arresto asincrono non sono supportati. È un errore inviare un evento di arresto asincrono.  
  
## <a name="discussion"></a>Discussione  
 L'effettiva implementazione degli eventi dipende dalla progettazione del DE. Il tipo di ogni evento inviato è determinato dai relativi attributi, che vengono impostati quando si progetta il DE. Ad esempio, una DE può inviare un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) come un evento asincrono, mentre un altro può inviarlo come un evento di arresto.  
  
 Nella tabella seguente vengono specificati i parametri del programma e del thread necessari per gli eventi, nonché i tipi di evento. Qualsiasi evento può essere sincrono. Nessun evento deve essere sincrono.  
  
> [!NOTE]
> L'interfaccia [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) è obbligatoria per tutti gli eventi.  
  
|Event|IDebugProgram2|IDebugThread2|Arresto di eventi|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obbligatoria|Obbligatoria|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non consentito|Non consentito|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non consentito|Non consentito|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|Può essere|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|Può essere|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|Può essere|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Necessario|Consentito, ma non obbligatorio|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Necessario|Consentito, ma non obbligatorio|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Necessario|Consentito, ma non obbligatorio|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Necessario|Consentito, ma non obbligatorio|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Necessario|Consentito, ma non obbligatorio|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|IDebugStopCompleteEvent2|Obbligatoria|Obbligatoria|Sì|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obbligatoria|Obbligatoria|Sì|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obbligatoria|Obbligatoria|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obbligatoria|Obbligatoria|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)
