---
title: Interfacce di base | Microsoft Docs
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
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ff260b8b54e3aff37b9cbceffaa1e4b3a374556
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49217737"
---
# <a name="core-interfaces"></a>Interfacce di base
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Le interfacce seguenti sono le interfacce di base per l'estensione del debugger utilizzando il [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Discussione  
 Queste interfacce vengono usate principalmente per creare il motore di debug (DE). Essi sono organizzate per categorie:  
  
-   [Punti di interruzione](#Breakpoints)  
  
-   [Contesti](#Contexts)  
  
-   [In modalità Server Core](#CoreServer)  
  
-   [Motori di debug](#DebugEngines)  
  
-   [Documenti](#Documents)  
  
-   [Eventi](#Events)  
  
-   [Espressioni](#Expressions)  
  
-   [Memoria](#Memory)  
  
-   [Moduli](#Modules)  
  
-   [Porte](#Ports)  
  
-   [Processi](#Processes)  
  
-   [Programmi](#Programs)  
  
-   [Proprietà](#Properties)  
  
-   [Stack frame](#StackFrames)  
  
-   [Thread](#Threads)  
  
-   [Visualizzatori di tipi](#TypeVisualizers)  
  
 Le entità che possono implementare le interfacce sono:  
  
-   Eseguire il debug del motore (DE)  
  
-   Fornitore di porte (PS)  
  
-   Analizzatore di espressioni (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> Punti di interruzione  
 Queste interfacce sono correlate per l'implementazione e il rilevamento di punti di interruzione.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Rappresenta un punto di interruzione associato a una posizione di memoria.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Inviato dal DE quando un punto di interruzione è associata a una posizione di memoria.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Rappresenta un checksum di documento per una richiesta di punto di interruzione.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Inviato dal DE quando un punto di interruzione non riesce a essere associato a una posizione di memoria.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato dal DE quando viene raggiunto un punto di interruzione.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Rappresenta una richiesta per un punto di interruzione; usato nella creazione di un punto di interruzione in sospeso.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Rappresenta una richiesta per un punto di interruzione; usato nella creazione di un punto di interruzione in sospeso.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Rappresenta le informazioni utilizzate per associare un punto di interruzione.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato dal DE quando non è associato un punto di interruzione da una posizione di memoria.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Rappresenta un punto di interruzione non valido (restituito da `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Rappresenta le informazioni di risoluzione su un punto di interruzione non valido.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Rappresenta una posizione in una funzione in cui è impostato un punto di interruzione.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Rappresenta un punto di interruzione che deve essere associato; usato nella creazione di un punto di interruzione associato.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione associati.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Rappresenta un'enumerazione su un set di punti di interruzione che non è stato possibile associare a una posizione di memoria.|  
  
##  <a name="Contexts"></a> Contesti  
 Queste interfacce rappresentano vari tipi di contesti all'interno del programma in fase di debug.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Rappresenta la posizione iniziale di un'istruzione di codice.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Estende la [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaccia per abilitare il recupero delle interfacce di modulo e processo.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL STUDIO, DE|Rappresenta una posizione in un documento.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta il contesto in cui valutare un'espressione.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta la posizione iniziale nella memoria di una raccolta di byte.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto del frame dello stack in un punto di interruzione o eccezione.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un contesto del frame dello stack in un punto di interruzione o eccezione.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Rappresenta un'enumerazione su un set di contesti di codice.|  
  
##  <a name="CoreServer"></a> In modalità Server Core  
 Queste interfacce rappresentano il computer in cui è viene eseguito il debug di un programma. Questi vengono implementati da [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ma può essere chiamato dai motori di debug.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Fornisce accesso alle porte e fornitori di porte, nonché informazioni relative al computer.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Rappresenta un' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) che supporta il debug remoto.|  
  
##  <a name="DebugEngines"></a> Motori di debug  
 Queste interfacce rappresentano motori di debug e i relativi eventi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Rappresenta un motore di debug personalizzato.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Rappresenta un motore di debug personalizzato che supporta il caricamento dei simboli, JustMyCode ed eccezioni.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza della DE per indicare che è pronto per gestire le attività di debug.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Rappresenta un motore di debug personalizzato che supporta l'avvio programmi.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|GERMANIA, PS|Rappresenta un nodo di programma che gestisce più motori di debug.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Fornisce un modo per il modello SDM ottenere un'interfaccia per il motore di debug da un thread, programma o dello stack frame.|  
  
##  <a name="Documents"></a> Documenti  
 Queste interfacce rappresentano i documenti (file di origine) e degli elementi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato dal DE per richiedere un documento da aprire.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Rappresenta un flusso di istruzioni disassemblate da un documento.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VISUAL STUDIO, DE|Rappresenta un documento fornito da DE, specificando un nome e un ID di classe (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|GERMANIA, EE|Rappresenta un checksum per un documento di debug e consente di passare il valore di checksum tra componenti.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VISUAL STUDIO, DE|Rappresenta un contesto di documento, una posizione all'interno di un documento corrispondente a un particolare contesto di istruzione e il codice.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VISUAL STUDIO, DE|Rappresenta una posizione generale all'interno di un documento.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Rappresenta una posizione in un file di origine da un offset di carattere.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VISUAL STUDIO, DE|Rappresenta un documento di testo fornito dal DE (derivato da [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), specificando il testo effettivo.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Inviato dal DE per specificare le modifiche in un file di origine che si trova in memoria.|  
  
##  <a name="Events"></a> Eventi  
 Queste interfacce rappresentano tutti gli eventi che vengono inviati tra il DE e il gestore di sessione di debug (SDM).  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Inviato dal DE per richiedere un documento da aprire.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Il motore di debug (DE) invia questa interfaccia per la gestione del debug (SDM) per impostare lo stato della sessione a barre messaggio durante il caricamento di simboli.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Inviato dal DE durante un'interruzione del programma è stata completata.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Inviato dal DE quando è associato un punto di interruzione.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Inviato dal DE quando un punto di interruzione si verifica un errore da associare.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Inviato dal DE quando viene raggiunto un punto di interruzione.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Inviato dal DE quando non è associato un punto di interruzione.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Inviato dal DE per determinare se deve essere arrestata in una determinata posizione.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Inviato dal DE per specificare le modifiche in un file di origine che si trova in memoria.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Inviato da ogni nuova istanza della DE per indicare che è pronto per gestire le attività di debug.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Inviato dal DE per indicare che il programma sottoposto a debug è pronto per l'esecuzione della prima istruzione.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Interfaccia che viene usata da altre interfacce eventi, che potrebbero restituire un errore, per fornire messaggi di errore leggibile dall'utente.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|GERMANIA, PS|Interfaccia di base da cui tutti gli altri eventi le interfacce sono derivate.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|Rappresenta un'interfaccia implementata per il modello SDM al quale vengono inviati gli eventi (espressi come gli oggetti che implementano un'interfaccia evento specifico).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Inviato dal DE quando si è verificata un'eccezione nel programma sottoposto a debug.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato dal DE quando una valutazione dell'espressione asincrona è stata completata.|  
|IDebugFindSymbolEvent2||OBSOLETE. NON USARE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Inviato dal DE quando è stata completata l'elaborazione di un'eccezione intercettata.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Inviato dal DE quando un programma ha terminato il caricamento.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Inviato da DE per avere la visualizzazione dell'IDE di un messaggio informativo per l'utente.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato dal DE quando un modulo viene caricato o scaricato.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Segnali di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente per avvertire l'utente che non sono stati trovati per l'eseguibile avviato i simboli del debugger.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Inviato da DE per avere la visualizzazione IDE una stringa arbitraria.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VISUAL STUDIO, DE|Inviato da una porta per comunicare gli eventi porta a ogni listener.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|GERMANIA, PS|Inviati per la porta o DE quando è stato creato un processo.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|GERMANIA, PS|Inviato dalla porta o DE quando viene eliminato un processo.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|GERMANIA, PS|Inviati per la porta o DE quando è stato creato un programma.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|GERMANIA, PS|Inviato dalla porta o DE quando viene eliminato un programma.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Consente a un motore di debug eseguire l'override del comportamento predefinito del [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente quando si termina una sessione di debug.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Inviate dal motore di debug (DE) al gestore di sessione di debug (SDM) quando si modifica il nome di un programma.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando una nuova proprietà (rappresentato dal `IDebugProperty2` interface) è stato creato.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato dal DE quando una proprietà è stata eliminata definitivamente.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Inviato dal DE quando si esegue l'istruzione di o in una funzione in modo che il valore restituito può essere visualizzato correttamente.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|Consente di eseguire il debug motori per leggere le impostazioni delle metriche in modalità remota.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Inviato dal DE quando un passaggio in, failover o all'esterno di un'istruzione è stato completato.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Inviato dal DE per indicare l'esito positivo o negativo del caricamento dei simboli per un modulo.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato dal DE quando un thread è stato creato.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato dal DE quando un thread è stato eliminato.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato dal DE quando un thread è stato modificato il relativo nome.|  
  
##  <a name="Expressions"></a> Espressioni  
 Queste interfacce rappresentano le espressioni da valutare in un particolare contesto.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Rappresenta un'espressione da valutare. Ottenuto dal [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaccia.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Rappresenta un contesto in cui viene valutata un'espressione. Ottenuto dal [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Inviato dal DE quando una valutazione dell'espressione asincrona è stata completata.|  
  
##  <a name="Memory"></a> Memoria  
 Queste interfacce rappresentano infatti sequenze di byte in memoria.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Rappresenta una sequenza di byte in memoria che possono essere letti da o scritti.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Rappresenta una posizione in memoria di una sequenza di byte.|  
  
##  <a name="Modules"></a> Moduli  
 Queste interfacce rappresentano un modulo, che corrisponde a un file eseguibile o. File DLL.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Rappresenta un singolo file eseguibile o DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Rappresenta un' [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) che supporta i simboli.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Inviato dal DE quando un modulo viene caricato o scaricato.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Rappresenta le informazioni sul server di origine contenuto in un file PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Rappresenta un'enumerazione su un set di moduli che sono noti a un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> Porte  
 Queste interfacce rappresentano le porte e i fornitori di porte.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VISUAL STUDIO, PS|Rappresenta la porta predefinita nel computer locale.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|Consente a un motore di debug che utilizza DCOM per porre il [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente per assicurarsi che il firewall non blocca il debug remoto.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VISUAL STUDIO, PS|Rappresenta una porta.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Inviato da una porta per comunicare gli eventi porta a ogni listener.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Rappresenta una porta che consente di avviare e terminare i processi.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Usato per registrare e annullare la registrazione di programmi con una porta. consente alla porta tenere traccia delle applicazioni in corso il debug.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Rappresenta un'interfaccia utente personalizzata per la selezione della porta.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|Rappresenta una richiesta per una porta da cui non verrà creata una nuova porta o che si trova.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Rappresenta un fornitore di porte.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Rappresenta un fornitore di porte che può rendere persistenti le informazioni (Salva su disco) sulle porte è creato.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Consente il [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] dell'interfaccia utente per visualizzare il testo all'interno di **informazioni sul trasporto** sezione del **Connetti a processo** nella finestra di dialogo.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|Consente di eseguire query per informazioni relative al computer di destinazione.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VISUAL STUDIO, PS|Rappresenta un'enumerazione su un set di porte.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|Rappresenta un'enumerazione su un set di fornitori di porte.|  
  
##  <a name="Processes"></a> Processi  
 Queste interfacce rappresentano processi, un unico file eseguibile contenente uno o più programmi.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Rappresenta un processo in esecuzione in un computer.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Rappresenta un processo che supporta attivamente debug (usato per sostituire passaggio, continuare ed eseguire metodi sul [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|GERMANIA, PS|Inviati per la porta o DE quando è stato creato un processo.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|GERMANIA, PS|Inviato dalla porta o DE quando viene eliminato un processo.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Rappresenta un processo che deve tenere traccia di sessione di cui è collegata a esso.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Rappresenta un'enumerazione di una serie di processi su una porta.|  
  
##  <a name="Programs"></a> Programmi  
 Queste interfacce rappresentano i programmi, unità logiche di esecuzione che non corrispondono necessariamente a un modulo o un eseguibile fisico.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Rappresenta un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che deve interagire con altri programmi in fase di debug nello stesso momento.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|GERMANIA, PS|Rappresenta un'unità logica di esecuzione.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|GERMANIA, PS|Inviati per la porta o DE quando è stato creato un programma.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|GERMANIA, PS|Inviato dalla porta o DE quando viene eliminato un programma.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|GERMANIA, PS|Rappresenta un' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che può essere gestita da più motori di debug.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Rappresenta un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che deve essere in grado di tenere traccia di sessione di cui è collegata a esso.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|GERMANIA, PS|Rappresenta un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che può restituire informazioni sul processo in cui è in esecuzione.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|GERMANIA, PS|Rappresenta un programma che è possibile eseguire il debug.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|GERMANIA, PS|Consente a un nodo di programma ricevere una notifica di un tentativo di collegare al programma associato.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Fornisce un modo per il modello SDM eseguire una query un CRI sui programmi controllate da tale DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|Usato da DEs per registrare i programmi con il modello SDM per mostrare che sono in fase di debug.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|GERMANIA, PS|Rappresenta un' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) che può effettuare il marshalling di interfacce attraverso i limiti di thread o processo.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|GERMANIA, PS|Rappresenta un'enumerazione di un set di programmi.|  
  
##  <a name="Properties"></a> Proprietà  
 Queste interfacce rappresentano le proprietà, un valore associato a un contesto specifico, in genere il risultato della valutazione di un'espressione.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Rappresenta un' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) in grado di visualizzare il relativo valore in modo personalizzato.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Rappresenta un valore di uno stack frame, documento o il risultato della valutazione di un'espressione.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Rappresenta un' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) che supporta le stringhe lunghe arbitrarie.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Inviato da DE quando una nuova proprietà (rappresentato dal [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface) è stato creato.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Inviato dal DE quando una proprietà è stata eliminata definitivamente.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Rappresenta un riferimento a una proprietà che può trovarsi all'esterno di qualsiasi stack frame specifico.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Rappresenta un'enumerazione su un set di [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strutture che descrivono le variabili, registri, parametri ed espressioni.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Rappresenta un'enumerazione su un set di [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strutture.|  
  
##  <a name="StackFrames"></a> Stack frame  
 Queste interfacce rappresentano un frame dello stack, un contesto in cui un punto di interruzione o un'eccezione è stata eseguita.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Rappresenta un contesto in cui un punto di interruzione o un'eccezione è stata eseguita.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Rappresenta un' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) che può gestire intercettare le eccezioni.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Rappresenta un'enumerazione dell'insieme delle [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) strutture che specificano la funzione chiamata sequenza utilizzata per arrivare a un determinato stack frame.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Rappresenta un'enumerazione su un set di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture che descrivono gli stack frame.|  
  
##  <a name="Threads"></a> Thread  
 Queste interfacce rappresentano i thread e i relativi eventi associati.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Rappresenta un thread di esecuzione.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Inviato dal DE quando un thread è stato creato.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Inviato dal DE quando un thread è stato eliminato.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Inviato dal DE quando un thread è stato modificato il relativo nome.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Rappresenta un'enumerazione su un set di thread.|  
  
##  <a name="TypeVisualizers"></a> Visualizzatori di tipi  
 Queste interfacce forniscono supporto per i visualizzatori di tipo. Queste interfacce vengono in genere implementate da un analizzatore di espressioni.  
  
|Interfaccia|Implementato da|Descrizione|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Rappresenta una matrice di byte da inviare a un visualizzatore di tipi.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Fornisce metodi per l'accesso ai dati deve essere passato a un visualizzatore di tipi.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Rappresenta una proprietà che fornisce accesso ai [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Creazione di un motore di debug personalizzato](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

