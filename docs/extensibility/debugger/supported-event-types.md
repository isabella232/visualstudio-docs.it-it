---
title: Tipi di evento supportati | Microsoft Docs
description: Informazioni sui tipi di evento supportati Visual Studio debug, inclusi gli eventi asincroni, gli eventi sincroni e gli eventi di arresto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 1fdd8cde2628a76c700e29b58885e45ff608fe0b3043df8b26e161a748066eaa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388903"
---
# <a name="supported-event-types"></a>Tipi di evento supportati
Visual Studio debug supporta attualmente i tipi di evento seguenti:

- Eventi asincroni

   Notificare al gestore di debug della sessione (SDM) e all'IDE che lo stato dell'applicazione in fase di debug sta cambiando. Questi eventi vengono elaborati nel tempo libero di SDM e dell'IDE. Non viene inviata alcuna risposta al motore di debug dopo l'elaborazione dell'evento. Le [interfacce IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sono esempi di eventi asincroni.

- Eventi sincroni

   Notificare a SDM e IDE che lo stato dell'applicazione in fase di debug sta cambiando. L'unica differenza tra questi eventi ed eventi asincroni è che una risposta viene inviata tramite il [metodo ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   L'invio di un evento sincrono è utile se è necessario che l'IDE continui l'elaborazione dopo la ricezione e l'elaborazione dell'evento da parte dell'IDE.

- Eventi di arresto sincrono o eventi di arresto

   Notificare a SDM e all'IDE che l'applicazione in fase di debug ha interrotto l'esecuzione del codice. Quando si invia un evento di arresto tramite il metodo [Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md), il [parametro IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) è obbligatorio. Gli eventi di arresto vengono continuati da una chiamata a uno dei metodi seguenti:

  - [Eseguire](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continua](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Le interfacce [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sono esempi di eventi di arresto.

  > [!NOTE]
  > Gli eventi di arresto asincroni non sono supportati. È un errore inviare un evento di arresto asincrono.

## <a name="discussion"></a>Discussione
 L'implementazione effettiva degli eventi dipende dalla progettazione del de. Il tipo di ogni evento inviato è determinato dai relativi attributi, che vengono impostati quando si progetta il de. Ad esempio, un DE può inviare [un IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) come evento asincrono, mentre un altro può inviarlo come evento di arresto.

 Nella tabella seguente vengono specificati i parametri del programma e del thread necessari per gli eventi e i tipi di evento. Qualsiasi evento può essere sincrono. Nessun evento deve essere sincrono.

> [!NOTE]
> [L'interfaccia IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) è necessaria per tutti gli eventi.

|Evento|IDebugProgram2|IDebugThread2|Arresto di eventi|
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
- [Invio di eventi](../../extensibility/debugger/sending-events.md)
