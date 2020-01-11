---
title: 'Procedura: creare una condizione della regola dichiarativa (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849327"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procedura: creare una condizione della regola dichiarativa (legacy)
In questo argomento viene descritto come dichiarare una condizione della regola usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un'istruzione Condition restituisce **true** o **false**. Una condizione della regola dichiarativa è un'istruzione della condizione creata tramite la finestra di [dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e archiviata come XML con il flusso di lavoro. Può includere predicati che confrontano lo stato del flusso di lavoro con l'algebra booleana che combina più predicati.

 Le condizioni di regole dichiarative vengono usate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Per creare una condizione di regole dichiarative usando l’Editor della condizione della regola

1. Nella finestra **Proprietà** dell'attività fare clic sulla proprietà **Condition** o sulla proprietà **UntilCondition** , a seconda dell'attività.

2. Selezionare la **condizione della regola dichiarativa** dall'elenco per la proprietà.

3. Espandere la proprietà **Condition** o **UntilCondition** .

4. Fare clic sulla proprietà **ConditionName** .

5. Fare clic sui puntini di sospensione **[...]** per **aprire la finestra** di dialogo **Seleziona condizione** .

6. Fare clic su **nuova condizione** per aprire la finestra di dialogo **Editor condizione della regola** .

7. Digitare l'espressione per la condizione nella casella di testo **condizione** .

     Per informazioni su come creare espressioni di condizione, vedere [finestra di dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Al termine della creazione dell'espressione della condizione, fare clic su **OK** per chiudere la finestra di dialogo e creare la condizione della regola con un nome assegnato.

     Verrà visualizzata la finestra di dialogo **Seleziona condizione** .

     Per informazioni sull'utilizzo della finestra di dialogo **Seleziona condizione** , vedere finestra di [dialogo Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) [che usano ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) [usando l'attività IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) [usando l'attività Replicator](https://msdn2.microsoft.com/library/bb628544.aspx) [usando la finestra di dialogo dell'editor della condizione della regola dell'attività While](https://msdn2.microsoft.com/library/bb628552.aspx) [(](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) legacy) finestra di dialogo [Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [con condizioni nei flussi di lavoro](https://msdn2.microsoft.com/library/bb628447.aspx)
