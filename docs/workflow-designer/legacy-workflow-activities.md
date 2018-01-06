---
title: "Attività flusso di lavoro legacy | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 756fa86cf892120b0062e2816f146425ac1b4fa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-workflow-activities"></a>Attività del flusso di lavoro legacy
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] include un set predefinito di attività che forniscono funzionalità per i flussi di controllo, le condizioni, la gestione degli eventi, la gestione degli stati e la comunicazione con applicazioni e servizi. Durante la progettazione di flussi di lavoro, è possibile usare le attività di sistema che sono fornite dalla [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] oppure è possibile creare attività personalizzate.  
  
 Nella tabella seguente è elencato il set di attività predefinito del framework di [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)]. Molte, ma non tutte, di queste attività sono rappresentati da finestre di progettazione di attività che è possibile accedere dal **della casella degli strumenti** del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Per creare un'attività, trascinare la finestra di progettazione dal **della casella degli strumenti** e rilasciarlo nell'area di progettazione.  
  
|Attività|Descrizione|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Utilizzato con il **HandleExternalEventActivity** attività per le comunicazioni di input e outpue con un servizio locale. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[Attività CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Usato per contenere la logica di pulizia per un'attività annullata prima che sia terminata l’esecuzione di tutti i figli dell’attività. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Consente di aggiungere codice di Visual Basic o di C# al flusso di lavoro. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Una versione compensabile del [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Una versione compensabile del **TransactionScopeActivity**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[Attività CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Consente di richiamare codice per annullare o compensare operazioni già eseguite dal flusso di lavoro quando si verifica un errore. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Wrapper per una o più attività che eseguono la compensazione per un'attività TransactionScopeActivity completata [!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [utilizzo dell'attività CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Esegue le attività figlio in base a una condizione che si applica al [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) attività stessa e in base alle condizioni che si applicano separatamente a ogni elemento figlio. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Consente di compilare ritardi nel flusso di lavoro basati su un intervallo di timeout. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Esegue il wrapping di una o di più attività eseguite quando si verifica un evento specificato. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Fornisce un framework per l'associazione di eventi a un'attività. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Esegue l'attività figlio contemporaneamente a un [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[Attività FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Usato per gestire un'eccezione di un tipo specificato. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[Attività FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Rappresenta un'attività composita che dispone di un elenco ordinato di attività figlio di tipo [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Usato in combinazione con il [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) attività per le comunicazioni di input e outpue con un servizio locale. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Verifica una condizione su ogni ramo ed esegue le attività sul primo ramo per il quale la condizione è uguale a **true**. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Rappresenta un ramo di un [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[Attività InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Consente al flusso di lavoro di richiamare un servizio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività attività InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[Attività InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Consente al flusso di lavoro di richiamare un altro flusso di lavoro. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Un'attività composita che contiene solo [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) attività figlio. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Fornisce una modalità per pianificare due o più figlio **SequenceActivity** rami di attività per l'elaborazione nello stesso momento. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[Attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Usare questa attività per rappresentare una raccolta di regole. Una regola è composta da condizioni e azioni risultanti. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Crea più istanze di un'unica attività figlio. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Fornisce una modalità semplice per collegare insieme più attività per l'esecuzione sequenziale. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in flusso di lavoro della macchina a stati. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Utilizzato un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) attività come contenitore per le attività figlio che vengono eseguite all'uscita di **StateActivity** attività. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Utilizzato un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) attività come contenitore per le attività figlio che vengono eseguite quando si immette il **StateActivity** attività. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Sospende l'operazione del flusso di lavoro per consentire di intervenire qualora si verifichino determinate condizioni di errore che richiedono attenzione speciale. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Esegue in sequenza le attività contenute in un dominio sincronizzato. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Consente di terminare immediatamente l'operazione del flusso di lavoro nel caso di una condizione di errore. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Consente di acquisire eccezioni aziendali generate come parte dei metadati di processo per un flusso di lavoro. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[L'attività TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Fornisce un framework per la gestione di transazioni ed eccezioni. Per ulteriori informazioni, vedere [utilizzo dell'attività TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[Attività WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Consente di definire l'occorrenza di un errore di servizio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività l'attività WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[Attività WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Riceve dati da un servizio Web. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[L'attività WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Risponde a una richiesta di servizio Web eseguita a un flusso di lavoro. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Consente al flusso di lavoro di eseguire ciclicamente fino a quando una condizione non viene soddisfatta. [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Utilizzo dell'attività l'attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)]come creare attività personalizzate, vedere [lo sviluppo di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65023) e [utilizzo dell'ActivityDesigner Legacy](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Visualizzazioni delle attività (legacy)](../workflow-designer/activity-views-legacy.md)  
 Descrive le diverse visualizzazioni di progettazione delle attività.  
  
 [Procedura: Aggiungere attività nella Casella degli strumenti (legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Illustra come aggiungere attività alla casella degli strumenti.  
  
 [Procedura: Creare una condizione della regola dichiarativa (legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Illustra la procedura per creare una condizione della regola dichiarativa.  
  
 [Procedura: Creare un set di regole per l'attività PolicyActivity (legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Illustra la procedura per creare un insieme di regole per l'attività PolicyActivity.  
  
 [Procedura: implementare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Illustra la procedura per implementare un'operazione del contratto [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
 [Procedura: richiamare un'operazione del contratto WCF (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Illustra la procedura per richiamare un'operazione del contratto [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Sviluppo di flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Lo sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65023)