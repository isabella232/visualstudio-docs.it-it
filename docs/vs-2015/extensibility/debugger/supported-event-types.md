---
title: Tipi di eventi supportati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c4297b1beaf93d82233eb756d0c812cc38e20c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839388"
---
# <a name="supported-event-types"></a>Tipi di evento supportati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debug in Visual Studio supporta attualmente i tipi di evento seguente:  
  
- Eventi asincroni  
  
   Inviare una notifica di gestore di sessione di debug (SDM) e IDE di modifica lo stato dell'applicazione in fase di debug. Questi eventi vengono elaborati con il tempo libero il modello SDM e dell'IDE. Nessuna risposta viene inviata al motore di debug (DE) dopo l'elaborazione dell'evento. Il [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) interfacce sono esempi di eventi asincroni.  
  
- Eventi sincroni  
  
   Inviare una notifica di SDM e IDE di modifica lo stato dell'applicazione in fase di debug. L'unica differenza tra questi eventi e gli eventi asincroni è che viene inviata la risposta tramite il [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) (metodo).  
  
   L'invio di un evento sincrono è utile se è necessario il DE per continuare l'elaborazione dopo che l'IDE riceve ed elabora l'evento.  
  
- Sincrono eventi di arresto o eventi di arresto  
  
   Notificare il modello SDM e dell'IDE che l'applicazione in fase di debug è stato arrestato l'esecuzione del codice. Quando si invia un evento di arresto tramite il metodo [evento](../../extensibility/debugger/reference/idebugeventcallback2-event.md), il [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) parametro è obbligatorio. Gli eventi di arresto proseguono da una chiamata a uno dei metodi seguenti:  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono riportati alcuni esempi di eventi di arresto.  
  
  > [!NOTE]
  >  Gli eventi di arresto asincrona non sono supportati. È un errore per inviare un evento di arresto asincrona.  
  
## <a name="discussion"></a>Discussione  
 L'implementazione effettiva degli eventi dipende dalla progettazione del DE. Il tipo di ogni evento inviato è determinato dai relativi attributi, che vengono impostate quando si progetta il DE. Ad esempio, può inviare un Germania un' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) come un evento asincrono, mentre un altro può inviare i dati come un evento di arresto.  
  
 Nella tabella seguente specifica i parametri che programma e i thread sono necessari per quali eventi, nonché i tipi di eventi. Qualsiasi evento può essere sincrono. Nessun evento deve essere sincrono.  
  
> [!NOTE]
>  Il [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfaccia è necessaria per tutti gli eventi.  
  
|event|IDebugProgram2|IDebugThread2|Eventi di arresto|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Non è consentita|Non è consentita|No|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Non è consentita|Non è consentita|No|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|Può essere|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|Può essere|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|Può essere|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obbligatorio|È consentito, ma non richiesto|No|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obbligatorio|È consentito, ma non richiesto|No|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obbligatorio|È consentito, ma non richiesto|No|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obbligatorio|È consentito, ma non richiesto|No|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obbligatorio|È consentito, ma non richiesto|No|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|IDebugStopCompleteEvent2|Obbligatorio|Obbligatorio|Yes|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obbligatorio|Obbligatorio|Yes|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obbligatorio|Obbligatorio|No|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|È consentito, ma non richiesto|È consentito, ma non richiesto|No|  
  
## <a name="see-also"></a>Vedere anche  
 [Invio di eventi](../../extensibility/debugger/sending-events.md)

