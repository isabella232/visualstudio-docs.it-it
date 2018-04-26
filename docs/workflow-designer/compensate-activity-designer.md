---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Compensate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8278066a12df0d195770391d0b2f3144ba16487d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="compensate-activity-designer"></a>ActivityDesigner Compensate

Il **compensa** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Compensate> attività.

## <a name="the-compensate-activity"></a>Attività Compensate
 L'attività <xref:System.Activities.Statements.Compensate> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Compensate> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Compensate.Target%2A>.

 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-compensate-activity-designer"></a>Utilizzo dell'ActivityDesigner Compensate
 Il **compensa** ActivityDesigner sono reperibili il **transazione** categoria del **casella degli strumenti**. Per aprire **casella degli strumenti**, selezionare il **casella degli strumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista**menu oppure premere CTRL + ALT + X.)

 Il **compensa** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Rilascio dell'ActivityDesigner crea un <xref:System.Activities.Statements.Compensate> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> compensate. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **compensa** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-compensate-properties"></a>Proprietà di Compensate
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia proprietà o nell'area di progettazione flussi di lavoro. Modificare il <xref:System.Activities.Statements.Compensate.Target%2A> proprietà nella griglia delle proprietà.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Compensate>. L'impostazione predefinita è Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Activity Designer Compensate](../workflow-designer/compensate-activity-designer.md)
- [Conferma](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)