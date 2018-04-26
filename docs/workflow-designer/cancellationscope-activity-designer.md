---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner CancellationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0f9a40434821294384154ddcbbfebbd0a7885eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope

Il **CancellationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CancellationScope> attività.

## <a name="the-cancellationscope-activity"></a>Attività CancellationScope
 L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope
 Il **CancellationScope** ActivityDesigner sono reperibili le **transazione** categoria di **casella degli strumenti**. Per aprire **casella degli strumenti**, selezionare il **casella degli strumenti** scheda della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.

 Il **CancellationScope** da, è possibile trascinare l'ActivityDesigner **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Eliminazione di **CancellationScope** ActivityDesigner crea un <xref:System.Activities.Statements.CancellationScope> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> cancellationscope. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore nell'intestazione del **CancellationScope** ActivityDesigner. È anche possibile modificarlo nel **DisplayName** finestra alla griglia delle proprietà.

### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà ma le altre proprietà deve essere modificata nell'area di progettazione flussi di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere la <xref:System.Activities.Statements.CancellationScope.Body%2A> attività, trascinare un'attività dalla **casella degli strumenti** nel **corpo** casella il **CancellationScope** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Specifica l'attività eseguita se è presente un annullamento. Per aggiungere la <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> attività, trascinare un'attività dalla **casella degli strumenti** nel **CancellationHandler** casella il **CancellationScope** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Conferma](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)