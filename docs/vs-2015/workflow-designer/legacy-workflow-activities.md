---
title: Attività flusso di lavoro legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6ff21a431e380a281ce1261215367b89c4ecf1a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205410"
---
# <a name="legacy-workflow-activities"></a>Attività del flusso di lavoro legacy
[!INCLUDE[wf](../includes/wf-md.md)] include un set predefinito di attività che forniscono funzionalità per i flussi di controllo, le condizioni, la gestione degli eventi, la gestione degli stati e la comunicazione con applicazioni e servizi. Durante la progettazione di flussi di lavoro, è possibile usare le attività di sistema che sono fornite dalla [!INCLUDE[wfd1](../includes/wfd1-md.md)] oppure è possibile creare attività personalizzate.  
  
 Nella tabella seguente è elencato il set di attività predefinito del framework di [!INCLUDE[wf2](../includes/wf2-md.md)]. Molte, ma non tutte, di queste attività sono rappresentate da ActivityDesigner ai quali è possibile accedere dal **casella degli strumenti** del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Per creare un'attività, trascinare la finestra di progettazione dal **casella degli strumenti** e rilasciarlo nell'area di progettazione.  
  
|Attività|Descrizione|  
|--------------|-----------------|  
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Utilizzato con il **HandleExternalEventActivity** attività per le comunicazioni di input e outpue con un servizio locale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|  
|[Attività CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Usato per contenere la logica di pulizia per un'attività annullata prima che sia terminata l’esecuzione di tutti i figli dell’attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|  
|[Attività CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Consente di aggiungere codice di Visual Basic o di C# al flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|  
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Una versione compensabile del [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|  
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Una versione compensabile del **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|  
|[Attività CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Consente di richiamare codice per annullare o compensare operazioni già eseguite dal flusso di lavoro quando si verifica un errore. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|  
|[Attività CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Un wrapper per una o più attività che eseguono la compensazione per un'attività TransactionScopeActivity completata [!INCLUDE[crdefault](../includes/crdefault-md.md)] [utilizzo dell'attività CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|  
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Esegue le attività figlio in base a una condizione che si applica al [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) attività stessa e in base alle condizioni che si applicano separatamente a ogni elemento figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|  
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Consente di compilare ritardi nel flusso di lavoro basati su un intervallo di timeout. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|  
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Esegue il wrapping di una o di più attività eseguite quando si verifica un evento specificato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
|[Attività EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Fornisce un framework per l'associazione di eventi a un'attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|  
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Esegue la propria attività figlio principale contemporaneamente a un' [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|  
|[Attività FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Usato per gestire un'eccezione di un tipo specificato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|  
|[Attività FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Rappresenta un'attività composita che dispone di un elenco ordinato di attività figlio di tipo [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|  
|[Attività HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Usato in combinazione con il [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) attività per le comunicazioni di input e outpue con un servizio locale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività HandleExternalEvent](http://go.microsoft.com/fwlink?LinkID=65073).|  
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Verifica una condizione su ogni ramo ed esegue le attività sul primo ramo per cui la condizione uguale **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|  
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Rappresenta un ramo di un' [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|  
|[Attività InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Consente al flusso di lavoro di richiamare un servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|  
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Consente al flusso di lavoro di richiamare un altro flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|  
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Un'attività composita contenente solo [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) attività figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|  
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Consente di pianificare due o più figlio **SequenceActivity** rami di attività per l'elaborazione nello stesso momento. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|  
|[Attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Usare questa attività per rappresentare una raccolta di regole. Una regola è composta da condizioni e azioni risultanti. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|  
|[Attività ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Crea più istanze di un'unica attività figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|  
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Fornisce una modalità semplice per collegare insieme più attività per l'esecuzione sequenziale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|  
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|[Attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in flusso di lavoro della macchina a stati. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Utilizzato in una [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) come contenitore per attività figlio che vengono eseguite all'uscita il **StateActivity** attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Utilizzato in una [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite quando si immettono le **StateActivity** attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|  
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Sospende l'operazione del flusso di lavoro per consentire di intervenire qualora si verifichino determinate condizioni di errore che richiedono attenzione speciale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|  
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Esegue in sequenza le attività contenute in un dominio sincronizzato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|  
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Consente di terminare immediatamente l'operazione del flusso di lavoro nel caso di una condizione di errore. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|  
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Consente di acquisire eccezioni aziendali generate come parte dei metadati di processo per un flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|  
|[L'attività TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Fornisce un framework per la gestione di transazioni ed eccezioni. Per altre informazioni, vedere [utilizzo dell'attività TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|  
|[Attività WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Consente di definire l'occorrenza di un errore di servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|  
|[Attività WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Riceve dati da un servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|  
|[Attività WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Risponde a una richiesta di servizio Web eseguita a un flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|  
|[Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Consente al flusso di lavoro di eseguire ciclicamente fino a quando una condizione non viene soddisfatta. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Utilizzo dell'attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] come creare attività personalizzate, vedere [sviluppo di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65023) e [utilizzo dell'ActivityDesigner Legacy](../workflow-designer/using-the-legacy-activity-designer.md).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Visualizzazioni delle attività (legacy)](../workflow-designer/activity-views-legacy.md)  
 Descrive le diverse visualizzazioni di progettazione delle attività.  
  
 [Procedura: Aggiungere attività nella Casella degli strumenti (legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md)  
 Illustra come aggiungere attività alla casella degli strumenti.  
  
 [Procedura: Creare una condizione della regola dichiarativa (legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md)  
 Illustra la procedura per creare una condizione della regola dichiarativa.  
  
 [Procedura: Creare un set di regole per l'attività PolicyActivity (legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)  
 Illustra la procedura per creare un insieme di regole per l'attività PolicyActivity.  
  
 [Procedura: Implementare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)  
 Illustra la procedura per implementare un'operazione del contratto [!INCLUDE[indigo2](../includes/indigo2-md.md)].  
  
 [Procedura: Richiamare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)  
 Illustra la procedura per richiamare un'operazione del contratto [!INCLUDE[indigo2](../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Windows Workflow Foundation](http://go.microsoft.com/fwlink?LinkID=65005)   
 [Sviluppo di flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65010)   
 [Sviluppo di attività del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65023)