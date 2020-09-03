---
title: ActivityDesigner Progettazione flussi di lavoro-CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597100"
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity

L'ActivityDesigner **CompensableActivity** viene usato per creare e configurare un' <xref:System.Activities.Statements.CompensableActivity> attività.

## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity
 L'ActivityDesigner **CompensableActivity** è disponibile nella categoria **transazione** della **casella degli strumenti**. Per aprire la **casella degli strumenti**, selezionare la scheda **casella degli strumenti** sul lato sinistro del progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

 È possibile trascinare l'ActivityDesigner **CompensableActivity** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro. È possibile trascinare l'ActivityDesigner all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.CompensableActivity> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore nell'intestazione dell'ActivityDesigner **CompensableActivity** . Può anche essere modificato nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di uso nella finestra di progettazione. La <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Activity%601.Result%2A> proprietà e può essere modificata nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Vero|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere l' <xref:System.Activities.Statements.CompensableActivity.Body%2A> attività, rilasciare un'attività dalla **casella degli strumenti** nella casella **corpo** dell'ActivityDesigner **CompensableActivity** . Aggiungere il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Falso|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l'attività, rilasciare la finestra di progettazione dalla **casella degli strumenti** nella casella **CancellationHandler** nell'ActivityDesigner **CompensableActivity** . Aggiungere il testo del suggerimento "rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Falso|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, trascinare l'ActivityDesigner dalla casella **degli strumenti** nella casella **CompensationHandler** nell'ActivityDesigner **CompensableActivity** . Aggiungere il testo del suggerimento "rilasciare l'attività".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Falso|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, trascinare l'ActivityDesigner dalla casella **degli strumenti** nella casella **ConfirmationHandler** nell'ActivityDesigner **CompensableActivity** . Aggiungere il testo del suggerimento "rilasciare l'attività".|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
