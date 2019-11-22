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
ms.openlocfilehash: e6bdfb5e2a51a274bd5f0490954a2825a2e488c5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302958"
---
# <a name="legacy-workflow-activities"></a>Attività del flusso di lavoro legacy
[!INCLUDE[wf](../includes/wf-md.md)] include un set predefinito di attività che forniscono funzionalità per il flusso di controllo, le condizioni, la gestione degli eventi, la gestione dello stato e la comunicazione con applicazioni e servizi. Durante la progettazione di flussi di lavoro, è possibile usare le attività di sistema che sono fornite dalla [!INCLUDE[wfd1](../includes/wfd1-md.md)] oppure è possibile creare attività personalizzate.

 Nella tabella seguente è elencato il set di attività predefinito del framework di [!INCLUDE[wf2](../includes/wf2-md.md)]. Molte, ma non tutte, di queste attività sono rappresentate da ActivityDesigner ai quali è possibile accedere dalla **Casella degli strumenti** di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Per creare un'attività, trascinare il relativo l'ActivityDesigner dalla **Casella degli strumenti** e rilasciarlo nell'area di progettazione.

|Attività|description|
|--------------|-----------------|
|[CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025)|Utilizzato con l'attività **HandleExternalEventActivity** per le comunicazioni di input e output con un servizio locale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65060).|
|[CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050)|Usato per contenere la logica di pulizia per un'attività annullata prima che sia terminata l’esecuzione di tutti i figli dell’attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65061).|
|[CodeActivity](https://go.microsoft.com/fwlink?LinkID=65026)|Consente di aggiungere codice di Visual Basic o di C# al flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][l'utilizzo dell'attività CodeActivity](https://go.microsoft.com/fwlink?LinkID=65062).|
|[CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65027)|Versione compensabile di [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CompensatableSequenceActivity](https://go.microsoft.com/fwlink?LinkID=65002).|
|[CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65051)|Versione compensabile di **TransactionScopeActivity**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività dell'CompensatableTransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65063).|
|[CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65052)|Consente di richiamare codice per annullare o compensare operazioni già eseguite dal flusso di lavoro quando si verifica un errore. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CompensateActivity](https://go.microsoft.com/fwlink?LinkID=65064).|
|[CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65053)|Wrapper per una o più attività che eseguono la compensazione per un'attività TransactionScopeActivity completata [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività CompensationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65065).|
|[ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)|Esegue le attività figlio in base a una condizione che si applica all'attività [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) stessa e in base a condizioni che si applicano separatamente a ogni elemento figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066).|
|[DelayActivity](https://go.microsoft.com/fwlink?LinkID=65028)|Consente di compilare ritardi nel flusso di lavoro basati su un intervallo di timeout. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività DelayActivity](https://go.microsoft.com/fwlink?LinkID=65067).|
|[EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029)|Esegue il wrapping di una o di più attività eseguite quando si verifica un evento specificato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65068).|
|[EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018)|Fornisce un framework per l'associazione di eventi a un'attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65069).|
|[EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65030)|Esegue l'attività figlio principale contemporaneamente a un [EventHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65018). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività EventHandlingScopeActivity](https://go.microsoft.com/fwlink?LinkID=65070).|
|[FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054)|Usato per gestire un'eccezione di un tipo specificato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65071).|
|[FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055)|Rappresenta un'attività composita che dispone di un elenco ordinato di attività figlio di tipo [FaultHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65054). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65072).|
|[HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65031)|Utilizzato in combinazione con l'attività [CallExternalMethodActivity](https://go.microsoft.com/fwlink?LinkID=65025) per le comunicazioni di input e output con un servizio locale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][utilizzando l'attività HandleExternalEventActivity](https://go.microsoft.com/fwlink?LinkID=65073).|
|[IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033)|Verifica una condizione su ogni ramo ed esegue le attività sul primo ramo per il quale la condizione è uguale a **true**. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65074).|
|[IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)|Rappresenta un ramo di un [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033). [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075).|
|[InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65035)|Consente al flusso di lavoro di richiamare un servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività InvokeWebServiceActivity](https://go.microsoft.com/fwlink?LinkID=65076).|
|[InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65036)|Consente al flusso di lavoro di richiamare un altro flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività InvokeWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65077).|
|[ListenActivity](https://go.microsoft.com/fwlink?LinkID=65037)|Attività composita che contiene solo attività figlio [EventDrivenActivity](https://go.microsoft.com/fwlink?LinkID=65029) . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività attività ListenActivity](https://go.microsoft.com/fwlink?LinkID=65078).|
|[ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65038)|Consente di pianificare due o più rami di attività figlio **SequenceActivity** per l'elaborazione contemporaneamente. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività ParallelActivity](https://go.microsoft.com/fwlink?LinkID=65079).|
|[PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019)|Usare questa attività per rappresentare una raccolta di regole. Una regola è composta da condizioni e azioni risultanti. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65004).|
|[ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)|Crea più istanze di un'unica attività figlio. [!INCLUDE[crdefault](../includes/crdefault-md.md)][l'utilizzo dell'attività ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65080).|
|[SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020)|Fornisce una modalità semplice per collegare insieme più attività per l'esecuzione sequenziale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65081).|
|[SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65041)|Specifica una transizione a un nuovo stato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività SetStateActivity](https://go.microsoft.com/fwlink?LinkID=65082).|
|[StateActivity](https://go.microsoft.com/fwlink?LinkID=65042)|Rappresenta uno stato in flusso di lavoro della macchina a stati. [!INCLUDE[crdefault](../includes/crdefault-md.md)][utilizzando l'attività StateActivity](https://go.microsoft.com/fwlink?LinkID=65083).|
|[StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65043)|Utilizzato in un'attività [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite quando si esce dall'attività **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività StateFinalizationActivity](https://go.microsoft.com/fwlink?LinkID=65008).|
|[StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65044)|Utilizzato in un'attività [StateActivity](https://go.microsoft.com/fwlink?LinkID=65042) come contenitore per le attività figlio che vengono eseguite quando si immette l'attività **StateActivity** . [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività StateInitializationActivity](https://go.microsoft.com/fwlink?LinkID=65006).|
|[SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65056)|Sospende l'operazione del flusso di lavoro per consentire di intervenire qualora si verifichino determinate condizioni di errore che richiedono attenzione speciale. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività SuspendActivity](https://go.microsoft.com/fwlink?LinkID=65084).|
|[SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65057)|Esegue in sequenza le attività contenute in un dominio sincronizzato. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività dell'SynchronizationScopeActivity](https://go.microsoft.com/fwlink?LinkID=65085).|
|[TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65058)|Consente di terminare immediatamente l'operazione del flusso di lavoro nel caso di una condizione di errore. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività TerminateActivity](https://go.microsoft.com/fwlink?LinkID=65086).|
|[ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65059)|Consente di acquisire eccezioni aziendali generate come parte dei metadati di processo per un flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività ThrowActivity](https://go.microsoft.com/fwlink?LinkID=65087).|
|[TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65093)|Fornisce un framework per la gestione di transazioni ed eccezioni. Per ulteriori informazioni, vedere [utilizzo dell'attività TransactionScopeActivity](https://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65046)|Consente di definire l'occorrenza di un errore di servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività WebServiceFaultActivity](https://go.microsoft.com/fwlink?LinkID=65089).|
|[WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65047)|Riceve dati da un servizio Web. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività WebServiceInputActivity](https://go.microsoft.com/fwlink?LinkID=65090).|
|[WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65048)|Risponde a una richiesta di servizio Web eseguita a un flusso di lavoro. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività WebServiceOutputActivity](https://go.microsoft.com/fwlink?LinkID=65092).|
|[WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)|Consente al flusso di lavoro di eseguire ciclicamente fino a quando una condizione non viene soddisfatta. [!INCLUDE[crdefault](../includes/crdefault-md.md)][usando l'attività dell'WhileActivity](https://go.microsoft.com/fwlink?LinkID=65091).|

 [!INCLUDE[crabout](../includes/crabout-md.md)] come creare attività personalizzate, vedere [sviluppo di attività personalizzate](https://go.microsoft.com/fwlink?LinkID=65023) e [uso dell'ActivityDesigner legacy](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Contenuto della sezione
 [Visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md) Descrive le diverse visualizzazioni di progettazione delle attività.

 [Procedura: aggiungere attività alla casella degli strumenti (legacy)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Viene illustrato come aggiungere attività alla casella degli strumenti.

 [Procedura: creare una condizione della regola dichiarativa (legacy)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Mostra i passaggi per creare una condizione della regola dichiarativa.

 [Procedura: creare un set di regole PolicyActivity (legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Mostra i passaggi per creare un set di regole PolicyActivity.

 [Procedura: implementare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Vengono illustrati i passaggi per implementare un'operazione del contratto [!INCLUDE[indigo2](../includes/indigo2-md.md)].

 [Procedura: richiamare un'operazione del contratto WCF (legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) Vengono illustrati i passaggi per richiamare un'operazione del contratto [!INCLUDE[indigo2](../includes/indigo2-md.md)].

## <a name="see-also"></a>Vedere anche
 [Windows Workflow Foundation attività](https://go.microsoft.com/fwlink?LinkID=65005) [sviluppo di flussi di lavoro](https://go.microsoft.com/fwlink?LinkID=65010) [sviluppo di attività del flusso](https://go.microsoft.com/fwlink?LinkID=65023) di lavoro