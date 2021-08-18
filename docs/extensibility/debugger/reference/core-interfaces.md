---
description: Le interfacce seguenti sono le interfacce di base per l'estensione del debugger tramite VS SDK.
title: Interfacce di base | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5dd69f5dd140118ea36ad02ff88bc36d6815616f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127649"
---
# <a name="core-interfaces"></a>Interfacce di base
Le interfacce seguenti sono le interfacce di base per l'estensione del debugger tramite [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Discussione
 Queste interfacce vengono usate principalmente per creare il motore di debug. Sono organizzati qui per categorie:

- [Punti di interruzione](#Breakpoints)

- [Contesti](#Contexts)

- [Core Server](#CoreServer)

- [Motori di debug](#DebugEngines)

- [Documents](#Documents) (Documenti)

- [Eventi](#Events)

- [Espressioni](#Expressions)

- [Memoria](#Memory)

- [Moduli](#Modules)

- [Ports](#Ports)

- [Processi](#Processes)

- [Programmi](#Programs)

- [Proprietà](#Properties)

- [Frame dello stack](#StackFrames)

- [Thread](#Threads)

- [Visualizzatori di tipi](#TypeVisualizers)

  Le entità che possono implementare le interfacce sono:

- Motore di debug (DE)

- Port Supplier (PS)

- Analizzatore di espressioni (edizione Enterprise)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a> Interruzione
 Queste interfacce sono correlate all'implementazione e al rilevamento dei punti di interruzione.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Rappresenta un punto di interruzione associato a una posizione di memoria.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Inviato da DE quando un punto di interruzione è associato a una posizione di memoria.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Rappresenta un checksum del documento per una richiesta di punto di interruzione.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Inviato da DE quando un punto di interruzione non viene associato a una posizione di memoria.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato da DE quando viene raggiunto un punto di interruzione.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Rappresenta una richiesta per un punto di interruzione. utilizzato nella creazione di un punto di interruzione in sospeso.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Rappresenta una richiesta per un punto di interruzione. utilizzato nella creazione di un punto di interruzione in sospeso.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Rappresenta le informazioni utilizzate per associare un punto di interruzione.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato da DE quando un punto di interruzione viene scollegato da una posizione di memoria.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Rappresenta un punto di interruzione non valido (restituito da `IDebugBreakpointErrorEvent2` ).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Rappresenta le informazioni di risoluzione relative a un punto di interruzione non valido.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Rappresenta una posizione in una funzione in cui è impostato un punto di interruzione.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Rappresenta un punto di interruzione che deve essere associato; utilizzato nella creazione di un punto di interruzione associato.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione associati.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione che non possono essere associati a una posizione di memoria.|

## <a name="contexts"></a><a name="Contexts"></a> Contesti
 Queste interfacce rappresentano vari tipi di contesti all'interno del programma di cui è in corso il debug.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Rappresenta la posizione iniziale di un'istruzione di codice.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Estende [l'interfaccia IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) per consentire il recupero delle interfacce del modulo e del processo.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL Studio, DE|Rappresenta una posizione in un documento.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta il contesto in cui valutare un'espressione.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta la posizione iniziale in memoria di una raccolta di byte.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto stack frame in corrispondenza di un punto di interruzione o di un'eccezione.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un contesto stack frame in corrispondenza di un punto di interruzione o di un'eccezione.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Rappresenta un'enumerazione su un set di contesti di codice.|

## <a name="core-server"></a><a name="CoreServer"></a> Server di base
 Queste interfacce rappresentano il computer in cui è in corso il debug di un programma. Questi vengono implementati [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] da ma possono essere chiamati in dai motori di debug.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fornisce l'accesso alle porte e ai fornitori di porte, nonché informazioni sul computer.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Rappresenta un [oggetto IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che supporta il debug remoto.|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Motori di debug
 Queste interfacce rappresentano i motori di debug e i relativi eventi associati.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Rappresenta un motore di debug personalizzato.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Rappresenta un motore di debug personalizzato che supporta il caricamento di simboli, JustMyCode ed eccezioni.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza del de per indicare che è pronto per gestire le attività di debug.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Rappresenta un motore di debug personalizzato che supporta l'avvio di programmi.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Rappresenta un nodo di programma che gestisce più motori di debug.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Consente a SDM di ottenere un'interfaccia al motore di debug da un thread, un programma o un stack frame.|

## <a name="documents"></a><a name="Documents"></a> Documenti
 Queste interfacce rappresentano i documenti (file di origine) e i relativi elementi associati.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato dal DE per richiedere l'apertura di un documento.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Rappresenta un flusso di istruzioni disassemblate da un documento.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|Visual Studio, DE|Rappresenta un documento fornito dal de, specificando un nome e un ID classe (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, edizione Enterprise|Rappresenta un checksum per un documento di debug e consente di passare il checksum tra i componenti.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|Visual Studio, DE|Rappresenta un contesto del documento, una posizione all'interno di un documento corrispondente a un'istruzione e a un contesto di codice specifici.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|Visual Studio, DE|Rappresenta una posizione generale all'interno di un documento.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Rappresenta una posizione in un file di origine come offset di caratteri.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|Visual Studio, DE|Rappresenta un documento di testo fornito da DE (derivato da [IDebugDocument2),](../../../extensibility/debugger/reference/idebugdocument2.md)fornendo il testo effettivo.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Inviato dal de per specificare le modifiche a un file di origine in memoria.|

## <a name="events"></a><a name="Events"></a> Eventi
 Queste interfacce rappresentano tutti gli eventi inviati tra de e la gestione del debug di sessione (SDM).

| Interfaccia | Implementato da | Descrizione |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Inviato dal DE per richiedere l'apertura di un documento. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Il motore di debug (DE) invia questa interfaccia al gestore di debug sessione (SDM) per impostare il messaggio della barra di stato durante il caricamento dei simboli. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Inviato dal De quando è stata completata un'interruzione del programma. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Inviato dal de quando viene associato un punto di interruzione. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Inviato dal de quando non è possibile eseguire l'associazione di un punto di interruzione. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Inviato dal de quando viene raggiunto un punto di interruzione. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Inviato dal de quando un punto di interruzione non è associato. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Inviato dal de per determinare se deve arrestarsi in una posizione specifica. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Inviato dal de per specificare le modifiche a un file di origine in memoria. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Inviato da ogni nuova istanza del de per indicare che è pronto per gestire le attività di debug. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Inviato dal DE per indicare che il programma in fase di debug è pronto per eseguire la prima istruzione. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Interfaccia utilizzata da altre interfacce eventi, che potrebbero restituire un errore, per fornire messaggi di errore leggibili dall'utente. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Interfaccia di base da cui derivano tutte le altre interfacce eventi. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | Rappresenta un'interfaccia implementata da SDM a cui vengono inviati gli eventi (espressi come oggetti che implementano una particolare interfaccia eventi). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Inviato dal de quando si è verificata un'eccezione nel programma di cui è in corso il debug. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Inviato dal de al termine di una valutazione asincrona dell'espressione. |
| IDebugFindSymbolEvent2 | | OBSOLETE. NON USARE. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Inviato dal DE quando l'elaborazione per un'eccezione intercettata è stata completata. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Inviato dal de al termine del caricamento di un programma. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Inviato dal de per fare in modo che l'IDE visualizza un messaggio informativo all'utente. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Inviato dal de quando un modulo viene caricato o scaricato. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Segnala [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] all'interfaccia utente del debugger di avvisare l'utente che non è stato possibile trovare simboli per l'eseguibile avviato. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Inviato dal de per fare in modo che l'IDE visualizza una stringa arbitraria. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | Visual Studio, DE | Inviato da una porta per comunicare gli eventi della porta a qualsiasi listener. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Inviato dal de o dalla porta quando è stato creato un processo. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Inviato dal de o dalla porta quando un processo è stato eliminato. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Inviato dal de o dalla porta quando è stato creato un programma. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Inviato dal de o dalla porta quando un programma è stato eliminato. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Consente a un motore di debug di eseguire l'override del comportamento predefinito dell'interfaccia [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utente quando si termina una sessione di debug. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Inviato dal motore di debug (DE) al gestore di debug della sessione (SDM) quando cambia il nome di un programma. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Inviato dal de quando è stata creata una nuova proprietà (rappresentata `IDebugProperty2` dall'interfaccia ). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Inviato dal de quando una proprietà è stata distrutta. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Inviato dal de quando si esce da o su una funzione in modo che il valore restituito possa essere visualizzato correttamente. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Consente ai motori di debug di leggere le impostazioni delle metriche in modalità remota. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Inviato dal DE quando è stata completata un'istruzione in, over o out di un'istruzione. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Inviato dal de per indicare l'esito positivo o negativo del caricamento dei simboli per un modulo. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Inviato dal de quando è stato creato un thread. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Inviato dal de quando un thread è stato eliminato. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Inviato dal de quando un thread ne ha modificato il nome. |

## <a name="expressions"></a>Espressioni <a name="Expressions"></a>
 Queste interfacce rappresentano espressioni da valutare in un contesto specifico.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Rappresenta un'espressione da valutare. Ottenuto [dall'interfaccia IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta un contesto in cui viene valutata un'espressione. Ottenuto [dall'interfaccia IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato da DE al termine di una valutazione asincrona dell'espressione.|

## <a name="memory"></a><a name="Memory"></a> Memoria
 Queste interfacce rappresentano sequenze di byte in memoria.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Rappresenta una sequenza di byte in memoria da cui è possibile leggere o scrivere.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta una posizione in memoria di una sequenza di byte.|

## <a name="modules"></a><a name="Modules"></a> Moduli
 Queste interfacce rappresentano un modulo, che corrisponde a un file eseguibile o .DLL file.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Rappresenta un singolo eseguibile o DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Rappresenta un [oggetto IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che supporta i simboli.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato da DE quando un modulo viene caricato o scaricato.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Rappresenta le informazioni sul server di origine contenute in un file PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Rappresenta un'enumerazione su un set di moduli noti da [un oggetto IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)|

## <a name="ports"></a><a name="Ports"></a> Porte
 Queste interfacce rappresentano porte e fornitori di porte.

| Interfaccia | Implementato da | Descrizione |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VISUAL Studio, PS | Rappresenta la porta predefinita nel computer locale. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Abilita un motore di debug che usa DCOM per chiedere all'interfaccia utente di assicurarsi che [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] il firewall non blocchi il debug remoto. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VISUAL Studio, PS | Rappresenta una porta. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Inviato da una porta per comunicare gli eventi della porta a qualsiasi listener. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Rappresenta una porta in grado di avviare e terminare processi. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Usato per registrare e annullare la registrazione di programmi con una porta. consente alla porta di tenere traccia dei programmi attualmente in fase di debug. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Rappresenta un'interfaccia utente personalizzata per la selezione della porta. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Rappresenta una richiesta per una porta da cui verrà creata o individuata una nuova porta. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Rappresenta un fornitore di porte. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Rappresenta un fornitore di porte in grado di rendere persistenti (salvare su disco) le informazioni sulle porte create. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Consente [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] all'interfaccia utente di visualizzare il testo **all'interno della sezione Informazioni** sul trasporto della **finestra di dialogo** Associa a processo . |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Consente di eseguire query per ottenere informazioni sul computer di destinazione. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VISUAL Studio, PS | Rappresenta un'enumerazione su un set di porte. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Rappresenta un'enumerazione su un set di fornitori di porte. |

## <a name="processes"></a><a name="Processes"></a> Processi
 Queste interfacce rappresentano i processi, un singolo eseguibile che contiene uno o più programmi.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Rappresenta un processo in esecuzione in un computer.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Rappresenta un processo che supporta attivamente il debug (usato per sostituire i metodi Step, Continue ed Execute [nell'interfaccia IDebugProgram2).](../../../extensibility/debugger/reference/idebugprogram2.md)|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Inviato da DE o dalla porta quando è stato creato un processo.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Inviato da DE o dalla porta quando un processo è stato eliminato.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Rappresenta un processo che deve tenere traccia della sessione associata.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Rappresenta un'enumerazione di un set di processi su una porta.|

## <a name="programs"></a><a name="Programs"></a> Programmi
 Queste interfacce rappresentano programmi, unità logiche di esecuzione che non corrispondono necessariamente a un eseguibile fisico o a un modulo.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Rappresenta un [oggetto IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che deve essere utilizzato insieme ad altri programmi di cui è in corso il debug contemporaneamente.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Rappresenta un'unità logica di esecuzione.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Inviato da DE o dalla porta quando è stato creato un programma.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Inviato da DE o dalla porta quando un programma è stato eliminato.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Rappresenta un [oggetto IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che può essere gestito da più motori di debug.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Rappresenta un [oggetto IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che deve essere in grado di tenere traccia della sessione associata.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Rappresenta un [oggetto IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che può restituire informazioni sul processo in cui è in esecuzione.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Rappresenta un programma di cui è possibile eseguire il debug.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Consente a un nodo di programma di ricevere una notifica di un tentativo di connessione al programma associato.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Consente a SDM di eseguire query su un de sui programmi controllati da tale DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Usato dai DE per registrare i programmi con SDM per mostrare che è in corso il debug.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Rappresenta un [oggetto IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) in grado di effettuare il marshalling delle interfacce attraverso i limiti del thread o del processo.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Rappresenta un'enumerazione di un set di programmi.|

## <a name="properties"></a><a name="Properties"></a> Proprietà
 Queste interfacce rappresentano le proprietà, un valore associato a un contesto specifico, in genere il risultato di una valutazione dell'espressione.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Rappresenta un [oggetto IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che può visualizzarne il valore in modo personalizzato.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Rappresenta un valore di un stack frame, un documento o il risultato di una valutazione dell'espressione.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Rappresenta un [oggetto IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che supporta stringhe arbitrariamente lunghe.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando è stata creata una nuova proprietà (rappresentata [dall'interfaccia IDebugProperty2).](../../../extensibility/debugger/reference/idebugproperty2.md)|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato da DE quando una proprietà è stata distrutta.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Rappresenta un riferimento a una proprietà che può esistere all'esterno di qualsiasi stack frame.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Rappresenta un'enumerazione su un set [di DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) che descrivono variabili, registri, parametri ed espressioni.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Rappresenta un'enumerazione su un set [di DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struttura .|

## <a name="stack-frames"></a><a name="StackFrames"></a> Stack frame
 Queste interfacce rappresentano un'stack frame, un contesto in cui si è verificata un'eccezione o un punto di interruzione.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto in cui si è verificata un'eccezione o un punto di interruzione.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un [oggetto IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) in grado di gestire le eccezioni intercettate.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Rappresenta un'enumerazione sul set [di CODE_PATH](../../../extensibility/debugger/reference/code-path.md) che specificano la sequenza di chiamata di funzione usata per arrivare a una determinata stack frame.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Rappresenta un'enumerazione su un set di [strutture FRAMEINFO,](../../../extensibility/debugger/reference/frameinfo.md) che descrivono gli stack frame.|

## <a name="threads"></a><a name="Threads"></a> Discussioni
 Queste interfacce rappresentano i thread e i relativi eventi associati.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Rappresenta un thread di esecuzione.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato dal de quando è stato creato un thread.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato dal de quando un thread è stato eliminato.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato dal de quando un thread ne ha modificato il nome.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Rappresenta un'enumerazione su un set di thread.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Visualizzatori di tipi
 Queste interfacce forniscono il supporto per i visualizzatori di tipi. Queste interfacce vengono in genere implementate da un analizzatore di espressioni.

|Interfaccia|Implementato da|Descrizione|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Rappresenta una matrice di byte da presentare a un visualizzatore di tipi.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fornisce metodi per ottenere l'accesso ai dati da passare a un visualizzatore di tipi.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Rappresenta una proprietà che fornisce l'accesso alle [implementazioni IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>Vedi anche
- [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Creazione di un motore di debug personalizzato](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
