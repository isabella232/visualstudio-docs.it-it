---
title: Tipi di evento supportati - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712806"
---
# <a name="supported-event-types"></a>Tipi di evento supportati
Il debug di Visual Studio supporta attualmente i seguenti tipi di evento:

- Eventi asincroni

   Notificare il gestore di sessione di debug (SDM) e IDE che lo stato dell'applicazione in fase di debug sta cambiando. Questi eventi vengono elaborati a piacere del modello SDM e dell'IDE. Nessuna risposta viene inviata al motore di debug (DE) dopo l'elaborazione dell'evento. Le interfacce [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sono esempi di eventi asincroni.

- Eventi sincroni

   Notificare il processo SDM e l'IDE che lo stato dell'applicazione sottoposta a debug sta cambiando. L'unica differenza tra questi eventi e gli eventi asincroni è che una risposta viene inviata tramite il [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metodo.

   L'invio di un evento sincrono è utile se è necessario che il DE continui l'elaborazione dopo che l'IDE riceve ed elabora l'evento.

- Eventi di arresto sincroni o eventi di arresto

   Notificare il file SDM e l'IDE che l'applicazione in fase di debug ha interrotto l'esecuzione del codice. Quando si invia un evento di arresto tramite il metodo [Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md), il parametro [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) è obbligatorio. Gli eventi di arresto continuano mediante una chiamata a uno dei seguenti metodi:

  - [Eseguire](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Passaggio](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continuare](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di arresto degli eventi.

  > [!NOTE]
  > Gli eventi di arresto asincroni non sono supportati. È un errore inviare un evento di arresto asincrono.

## <a name="discussion"></a>Discussione
 L'implementazione effettiva degli eventi dipende dalla progettazione del DE. Il tipo di ogni evento inviato è determinato dai relativi attributi, che vengono impostati quando si progetta il DE. Ad esempio, un DE può inviare un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) come evento asincrono, mentre un altro può inviarlo come evento di arresto.

 Nella tabella seguente vengono specificati i parametri del programma e del thread necessari per gli eventi, nonché i tipi di evento. Qualsiasi evento può essere sincrono. Nessun evento deve essere sincrono.

> [!NOTE]
> Il [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) interfaccia è necessaria per tutti gli eventi.

|Event|IDebugProgram2|IDebugThread2|Arresto degli eventi|
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
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obbligatoria|Consentito, ma non obbligatorio|No|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obbligatoria|Consentito, ma non obbligatorio|No|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obbligatoria|Consentito, ma non obbligatorio|No|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obbligatoria|Consentito, ma non obbligatorio|No|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obbligatoria|Consentito, ma non obbligatorio|No|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|
|IDebugStopCompleteEvent2|Obbligatoria|Obbligatoria|Sì|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obbligatoria|Obbligatoria|Sì|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obbligatoria|Obbligatoria|No|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obbligatoria|Obbligatoria|No|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Consentito, ma non obbligatorio|Consentito, ma non obbligatorio|No|

## <a name="see-also"></a>Vedere anche
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
