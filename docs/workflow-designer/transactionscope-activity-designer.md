---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner TransactionScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67c8a5c610492f298d3f2ef6de35444c96f7310f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="transactionscope-activity-designer"></a>ActivityDesigner TransactionScope

Il **TransactionScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.TransactionScope> attività.

## <a name="the-transactionscope-activity"></a>Attività TransactionScope
 L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta. Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.

### <a name="using-the-transactionscope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactionScope
 Il **TransactionScope** ActivityDesigner è reperibile nella **transazione** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**  scheda della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu o premere CTRL + ALT + X.)

 Il **TransactionScope** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **TransactionScope** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-transactionscope-properties"></a>Proprietà di TransactionScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Statements.TransactionScope.Body%2A> proprietà possono essere modificate nell'area di progettazione flussi di lavoro. Le altre proprietà devono invece essere modificate nella griglia delle proprietà.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>. Il valore predefinito è TransactionScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Consente di specificare l'attività da eseguire in un'unica transazione. Per aggiungere il <xref:System.Activities.Statements.TransactionScope.Body%2A> attività, trascinare un'attività dal **della casella degli strumenti** nel **corpo** casella il **TransactionScope** ActivityDesigner con testo di suggerimento "rilasciare l'attività di seguito".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Consente di specificare l'intervallo di tempo (nel formato 00:00:00, che indica ore:minuti:secondi) disponibile per il completamento della transazione. Il valore predefinito è 1 minuto (00:01:00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|True|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Conferma](../workflow-designer/confirm-activity-designer.md)