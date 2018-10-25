---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner CancellationScope
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
ms.openlocfilehash: d3b9e565e5579405fa73ea6a3de12d7c27ed7edc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926839"
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope

Il **CancellationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CancellationScope> attività.

## <a name="the-cancellationscope-activity"></a>Attività CancellationScope

L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope

Il **CancellationScope** ActivityDesigner è reperibile nella **transazione** categoria del **della casella degli strumenti**. Per aprire **casella degli strumenti**, selezionare la **della casella degli strumenti** scheda della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il **CancellationScope** ActivityDesigner può essere trascinato dalla **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Eliminazione il **CancellationScope** crea ActivityDesigner una <xref:System.Activities.Statements.CancellationScope> attività associata a un valore predefinito <xref:System.Activities.Activity.DisplayName%2A> cancellationscope. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore dell'intestazione del **CancellationScope** ActivityDesigner. È anche possibile modificarlo nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà ma le altre proprietà deve essere modificata nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere il <xref:System.Activities.Statements.CancellationScope.Body%2A> attività, rilasciare un'attività dalla **casella degli strumenti** nel **corpo** casella il **CancellationScope** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Specifica l'attività che viene eseguita se è presente un annullamento. Per aggiungere il <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> attività, rilasciare un'attività dalla **casella degli strumenti** nel **CancellationHandler** casella il **CancellationScope** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)