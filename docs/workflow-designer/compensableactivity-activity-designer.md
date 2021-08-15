---
title: ActivityDesigner CompensableActivity
description: Informazioni su come usare l'ActivityDesigner CompensableActivity in Progettazione flussi di lavoro creare e configurare un'attività CompensableActivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 0e7cf66a625260d5880edc39a685d7e7fa533ba454aabd16c93cdee82aae06d4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121314641"
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity

**L'ActivityDesigner CompensableActivity** viene usato per creare e configurare <xref:System.Activities.Statements.CompensableActivity> un'attività.

## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity
 **L'ActivityDesigner CompensableActivity** è disponibile nella categoria **Transazione** della Casella **degli strumenti**. Per aprire **casella degli** strumenti , **selezionare** la scheda Casella degli strumenti sul lato sinistro del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

 **L'ActivityDesigner CompensableActivity** può essere trascinato dalla casella **degli** strumenti e rilasciato nell Progettazione flussi di lavoro surface. È possibile eliminare l'ActivityDesigner all'interno di <xref:System.Activities.Statements.Sequence> un oggetto . L'eliminazione dell'ActivityDesigner crea <xref:System.Activities.Statements.CompensableActivity> un'attività con <xref:System.Activities.Activity.DisplayName%2A> l'impostazione predefinita CompensableActivity. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore nell'intestazione dell'ActivityDesigner **CompensableActivity.** Può anche essere modificato nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di uso nella finestra di progettazione. La proprietà e può essere modificata nella griglia delle proprietà, ma le altre proprietà devono essere modificate nella <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Activity%601.Result%2A> Progettazione flussi di lavoro proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Vero|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere <xref:System.Activities.Statements.CompensableActivity.Body%2A> l'attività, rilasciare un'attività dalla casella **degli** strumenti nella **casella Corpo** **dell'ActivityDesigner CompensableActivity.** Aggiungere il testo del suggerimento "Drop activity here".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Falso|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l'attività, rilasciare la finestra **di** progettazione dalla casella degli strumenti nella **casella CancellationHandler** dell'ActivityDesigner **CompensableActivity.** Aggiungere il testo del suggerimento "Drop Activity Here" (Rilascia attività qui).|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Falso|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, rilasciare il relativo ActivityDesigner dalla casella **degli** strumenti nella casella **CompensationHandler** dell'ActivityDesigner **CompensableActivity.** Aggiungere il testo del suggerimento "Drop Activity Here" (Rilascia attività qui).|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Falso|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, rilasciare il relativo ActivityDesigner **dalla** casella degli strumenti nella casella **ConfirmationHandler** dell'ActivityDesigner **CompensableActivity.** Aggiungere il testo del suggerimento "Drop Activity Here" (Rilascia attività qui).|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
