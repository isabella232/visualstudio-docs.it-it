---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7257e7cc31e0503c7e466bbf4f8c9dd02e5fe15a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836131"
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity

Il **CompensableActivity** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CompensableActivity> attività.

## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity
 Il **CompensableActivity** ActivityDesigner è reperibile nella **transazione** categoria del **della casella degli strumenti**. Per aprire **casella degli strumenti**, selezionare la **della casella degli strumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

 Il **CompensableActivity** ActivityDesigner può essere trascinato dalla **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro. Si è stato possibile eliminare l'area di progettazione di attività all'interno di un <xref:System.Activities.Statements.Sequence>. La finestra di progettazione di attività di rilascio crea un <xref:System.Activities.Statements.CompensableActivity> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> di CompensableActivity. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore dell'intestazione del **CompensableActivity** ActivityDesigner. Può anche essere modificato nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> proprietà può essere modificata nella griglia delle proprietà ma le altre proprietà deve essere modificata nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere il <xref:System.Activities.Statements.CompensableActivity.Body%2A> attività, rilasciare un'attività dalla **casella degli strumenti** nel **corpo** casella il **CompensableActivity** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Specifica l'attività che viene eseguito quando si verifica un annullamento. Per aggiungere l'attività, rilasciarne relativo l'ActivityDesigner dalla **casella degli strumenti** nel **CancellationHandler** nella casella il **CompensableActivity** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, rilasciarne relativi ActivityDesigner dalla **casella degli strumenti** nel **CompensationHandler** nella casella il **CompensableActivity** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, rilasciarne relativi ActivityDesigner dalla **casella degli strumenti** nel **ConfirmationHandler** nella casella il **CompensableActivity** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)