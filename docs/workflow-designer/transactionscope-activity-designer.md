---
title: ActivityDesigner Progettazione flussi di lavoro-TransactionScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8f9ed7822dc231fdd4888d3e44c4e3218357f95
ms.sourcegitcommit: d97d72308ef306e7f28c3a76913caee4ff450bbb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2020
ms.locfileid: "90713477"
---
# <a name="transactionscope-activity-designer"></a>ActivityDesigner TransactionScope

L'ActivityDesigner **TransactionScope** viene usato per creare e configurare un' <xref:System.Activities.Statements.TransactionScope> attività.

## <a name="the-transactionscope-activity"></a>Attività TransactionScope

L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta. Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.

### <a name="using-the-transactionscope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactionScope

Accedere all'ActivityDesigner **TransactionScope** nella categoria **transazione** della **casella degli strumenti**. È possibile trascinare l'ActivityDesigner **TransactionScope** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **TransactionScope** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-transactionscope-properties"></a>Proprietà di TransactionScope

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Le <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Statements.TransactionScope.Body%2A> proprietà e possono essere modificate in Progettazione flussi di lavoro area. Le altre proprietà devono invece essere modificate nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>. Il valore predefinito è TransactionScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Vero|Consente di specificare l'attività da eseguire in un'unica transazione. Per aggiungere l' <xref:System.Activities.Statements.TransactionScope.Body%2A> attività, rilasciare un'attività dalla casella **degli strumenti** nella casella **corpo** dell'ActivityDesigner **TransactionScope** con il testo di suggerimento "rilasciare l'attività".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Vero|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Falso|Consente di specificare l'intervallo di tempo (nel formato 00:00:00, che indica ore:minuti:secondi) disponibile per il completamento della transazione. Il valore predefinito è 1 minuto (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|Vero|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
