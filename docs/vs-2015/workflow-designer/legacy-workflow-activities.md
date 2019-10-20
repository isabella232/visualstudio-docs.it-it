---
title: Attività del flusso di lavoro legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4f1110424aefc1771c0dc7600fb9996bff0e892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658946"
---
# <a name="legacy-workflow-activities"></a>Attività del flusso di lavoro legacy
[!INCLUDE[wf](../includes/wf-md.md)] include un set predefinito di attività che forniscono funzionalità per i flussi di controllo, le condizioni, la gestione degli eventi, la gestione degli stati e la comunicazione con applicazioni e servizi. Durante la progettazione di flussi di lavoro, è possibile usare le attività di sistema che sono fornite dalla [!INCLUDE[wfd1](../includes/wfd1-md.md)] oppure è possibile creare attività personalizzate.

 Nella tabella seguente è elencato il set di attività predefinito del framework di [!INCLUDE[wf2](../includes/wf2-md.md)]. Molte, ma non tutte, di queste attività sono rappresentate da ActivityDesigner a cui è possibile accedere dalla **casella degli strumenti** del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Per creare un'attività, trascinare la relativa finestra di progettazione dalla **casella degli strumenti** e rilasciarla nell'area di progettazione.

|Attività|Descrizione|
|--------------|-----------------|
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Utilizzato con l'attività **HandleExternalEventActivity** per le comunicazioni di input e output con un servizio locale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Usato per contenere la logica di pulizia per un'attività annullata prima che sia terminata l’esecuzione di tutti i figli dell’attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|Consente di aggiungere codice di Visual Basic o di C# al flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][l'utilizzo dell'attività CodeActivity](http://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|Versione compensabile di [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65002).|
|[Dell'CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|Versione compensabile di **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività dell'CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Consente di richiamare codice per annullare o compensare operazioni già eseguite dal flusso di lavoro quando si verifica un errore. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|Wrapper per una o più attività che eseguono la compensazione per un'attività TransactionScopeActivity completata [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|Esegue le attività figlio in base a una condizione che si applica all'attività [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) stessa e in base a condizioni che si applicano separatamente a ogni elemento figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|Consente di compilare ritardi nel flusso di lavoro basati su un intervallo di timeout. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività DelayActivity](http://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Esegue il wrapping di una o di più attività eseguite quando si verifica un evento specificato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Fornisce un framework per l'associazione di eventi a un'attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Esegue l'attività figlio principale contemporaneamente a un [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Usato per gestire un'eccezione di un tipo specificato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|Rappresenta un'attività composita che dispone di un elenco ordinato di attività figlio di tipo [FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65031)|Utilizzato in combinazione con l'attività [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) per le comunicazioni di input e output con un servizio locale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][utilizzando l'attività HandleExternalEventActivity](http://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Verifica una condizione su ogni ramo ed esegue le attività sul primo ramo per il quale la condizione è uguale a **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Rappresenta un ramo di un [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Consente al flusso di lavoro di richiamare un servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|Consente al flusso di lavoro di richiamare un altro flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65077).|
|[Attività ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Attività composita che contiene solo attività figlio [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività attività ListenActivity](http://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Consente di pianificare due o più rami di attività figlio **SequenceActivity** per l'elaborazione contemporaneamente. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Usare questa attività per rappresentare una raccolta di regole. Una regola è composta da condizioni e azioni risultanti. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Crea più istanze di un'unica attività figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][l'utilizzo dell'attività ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Fornisce una modalità semplice per collegare insieme più attività per l'esecuzione sequenziale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in flusso di lavoro della macchina a stati. [!INCLUDE[crdefault](../includes/crdefault-md.md)][utilizzando l'attività StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Utilizzato in un'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite quando si esce dall'attività **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Utilizzato in un'attività [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite quando si immette l'attività **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Sospende l'operazione del flusso di lavoro per consentire di intervenire qualora si verifichino determinate condizioni di errore che richiedono attenzione speciale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65084).|
|[Dell'SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|Esegue in sequenza le attività contenute in un dominio sincronizzato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività dell'SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Consente di terminare immediatamente l'operazione del flusso di lavoro nel caso di una condizione di errore. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Consente di acquisire eccezioni aziendali generate come parte dei metadati di processo per un flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|Fornisce un framework per la gestione di transazioni ed eccezioni. Per ulteriori informazioni, vedere [utilizzo dell'attività TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Consente di definire l'occorrenza di un errore di servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Riceve dati da un servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65048)|Risponde a una richiesta di servizio Web eseguita a un flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività WebServiceOutputActivity](http://go.microsoft.com/fwlink?LinkID=65092).|
|[Dell'WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Consente al flusso di lavoro di eseguire ciclicamente fino a quando una condizione non viene soddisfatta. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività dell'WhileActivity](http://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] come creare attività personalizzate, vedere [sviluppo di attività personalizzate](http://go.microsoft.com/fwlink?LinkID=65023) e [uso dell'ActivityDesigner legacy](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md) Descrive le diverse visualizzazioni di progettazione delle attività.

 [Procedura: aggiungere attività alla casella degli strumenti (legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Viene illustrato come aggiungere attività alla casella degli strumenti.

 [Procedura: creare una condizione della regola dichiarativa (legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Mostra i passaggi per creare una condizione della regola dichiarativa.

 [Procedura: creare un set di regole PolicyActivity (legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Mostra i passaggi per creare un set di regole PolicyActivity.

 [Procedura: implementare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Vengono illustrati i passaggi per implementare un'operazione del contratto [!INCLUDE[indigo2](../includes/indigo2-md.md)].

 [Procedura: richiamare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Vengono illustrati i passaggi per richiamare un'operazione del contratto [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>Vedere anche
 [Windows Workflow Foundation attività](http://go.microsoft.com/fwlink?LinkID=65005) [sviluppo di flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65010) [sviluppo di attività del flusso](http://go.microsoft.com/fwlink?LinkID=65023) di lavoro