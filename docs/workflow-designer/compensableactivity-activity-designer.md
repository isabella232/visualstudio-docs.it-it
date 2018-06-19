---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner CompensableActivity
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
ms.openlocfilehash: fdab42766fd20989831e446a45115d17b3ee28fd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31978661"
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity

Il **CompensableActivity** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CompensableActivity> attività.

## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity
 Il **CompensableActivity** ActivityDesigner sono reperibili le **transazione** categoria di **casella degli strumenti**. Per aprire **casella degli strumenti**, selezionare il **casella degli strumenti** scheda sul lato sinistro della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.

 Il **CompensableActivity** da, è possibile trascinare l'ActivityDesigner **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro. Si è stato possibile eliminare la finestra di progettazione di attività all'interno di un <xref:System.Activities.Statements.Sequence>. Rilascio dell'ActivityDesigner crea un <xref:System.Activities.Statements.CompensableActivity> attività predefinito <xref:System.Activities.Activity.DisplayName%2A> di CompensableActivity. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore nell'intestazione del **CompensableActivity** ActivityDesigner. Possono anche essere modificata nel **DisplayName** finestra alla griglia delle proprietà.

### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> proprietà può essere modificata nella griglia delle proprietà ma le altre proprietà deve essere modificata nell'area di progettazione flussi di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere la <xref:System.Activities.Statements.CompensableActivity.Body%2A> attività, trascinare un'attività dalla **casella degli strumenti** nel **corpo** casella il **CompensableActivity** ActivityDesigner. Aggiungere il testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Specifica l'attività che viene eseguito quando viene eseguito un annullamento. Per aggiungere l'attività, rilasciarne relativo l'ActivityDesigner dalla **casella degli strumenti** nel **CancellationHandler** casella il **CompensableActivity** ActivityDesigner. Aggiungere testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, rilasciarne relativi ActivityDesigner dalla **casella degli strumenti** nel **CompensationHandler** casella il **CompensableActivity** ActivityDesigner. Aggiungere testo di suggerimento "Rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, rilasciarne relativi ActivityDesigner dalla **casella degli strumenti** nel **ConfirmationHandler** casella il **CompensableActivity** ActivityDesigner. Aggiungere testo di suggerimento "Rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Conferma](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)