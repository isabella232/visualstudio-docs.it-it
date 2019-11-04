---
title: ActivityDesigner CompensableActivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656998"
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity
L'ActivityDesigner **CompensableActivity** viene usato per creare e configurare un'attività <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity
 L'ActivityDesigner **CompensableActivity** è disponibile nella categoria **transazione** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti. dal menu **Visualizza** oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **CompensableActivity** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.CompensableActivity> con un elemento <xref:System.Activities.Activity.DisplayName%2A> predefinito di CompensableActivity. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **CompensableActivity** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di uso nella finestra di progettazione. È possibile modificare le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>, rilasciare un'attività dalla casella **degli strumenti** nella casella **corpo** dell'ActivityDesigner **CompensableActivity** con il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l'attività, rilasciare la finestra di progettazione dalla **casella degli strumenti** nella casella **CancellationHandler** nell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, trascinare l'ActivityDesigner dalla casella **degli strumenti** nella casella **CompensationHandler** nell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, trascinare l'ActivityDesigner dalla casella **degli strumenti** nella casella **ConfirmationHandler** nell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "drop Activity here".|

## <a name="see-also"></a>Vedere anche
 [Transazione](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) [Conferma](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)