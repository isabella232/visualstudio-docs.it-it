---
title: ActivityDesigner TransactionScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670184"
---
# <a name="transactionscope-activity-designer"></a>ActivityDesigner TransactionScope
L'ActivityDesigner **TransactionScope** viene usato per creare e configurare un'attività <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>Attività TransactionScope
 L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta. Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.

### <a name="using-the-transactionscope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactionScope
 L'ActivityDesigner **TransactionScope** è disponibile nella categoria **transazione** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti nella **visualizzazione** menu o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **TransactionScope** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **TransactionScope** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-transactionscope-properties"></a>Proprietà di TransactionScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Statements.TransactionScope.Body%2A> possono essere modificate nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Le altre proprietà devono invece essere modificate nella griglia delle proprietà.

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>. Il valore predefinito è TransactionScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Consente di specificare l'attività da eseguire in un'unica transazione. Per aggiungere l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A>, eliminare un'attività dalla casella **degli strumenti** nella casella **corpo** dell'ActivityDesigner **TransactionScope** con il testo di suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Consente di specificare l'intervallo di tempo (nel formato 00:00:00, che indica ore:minuti:secondi) disponibile per il completamento della transazione. Il valore predefinito è 1 minuto (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|

## <a name="see-also"></a>Vedere anche
 [Transazione](../workflow-designer/transaction-activity-designers.md) [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [compensate](../workflow-designer/compensate-activity-designer.md) [Confirm](../workflow-designer/confirm-activity-designer.md)