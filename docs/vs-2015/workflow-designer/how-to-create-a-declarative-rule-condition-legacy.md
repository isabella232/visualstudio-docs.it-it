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
ms.openlocfilehash: 2dc63fc58b22792e566df91bd86cac40e3fd2e65
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297485"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procedura: creare una condizione della regola dichiarativa (legacy)
In questo argomento viene descritto come dichiarare una condizione della regola usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un'istruzione Condition restituisce **true** o **false**. Una condizione della regola dichiarativa è un'istruzione della condizione creata tramite la finestra di [dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e archiviata come XML con il flusso di lavoro. Può includere predicati che confrontano lo stato del flusso di lavoro con l'algebra booleana che combina più predicati.

 Le condizioni di regole dichiarative vengono usate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Per creare una condizione di regole dichiarative usando l’Editor della condizione della regola

1. Nella finestra dell’attività **Proprietà**, fare clic sulla proprietà **Condizione** o sulla proprietà **UntilCondition** a seconda dell'attività.

2. Selezionare **Condizione di regole dichiarative** dall'elenco della proprietà.

3. Espandere la proprietà **Condizione** o **UntilCondition**.

4. Fare clic sulla proprietà **ConditionName**.

5. Fare clic sui puntini di sospensione **[…]** di **ConditionName** per aprire la finestra di dialogo **Seleziona condizione**.

6. Fare clic su **Nuova condizione** per aprire la finestra di dialogo **Editor condizione della regola**.

7. Digitare l'espressione per la condizione nella casella di testo **Condizione**.

     Per informazioni su come creare espressioni di condizione, vedere [finestra di dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Quando si è finito di creare l'espressione della condizione, fare clic su **OK** per chiudere la finestra di dialogo e creare la condizione della regola con un nome assegnato.

     Verrà visualizzata la finestra di dialogo **Seleziona condizione**.

     Per informazioni sull'utilizzo della finestra di dialogo **Seleziona condizione** , vedere finestra di [dialogo Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) [che usano ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65066) [usando l'attività IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65075) [usando l'attività Replicator](https://go.microsoft.com/fwlink?LinkID=65080) [usando la finestra di dialogo dell'editor della condizione della regola dell'attività While](https://go.microsoft.com/fwlink?LinkID=65091) [(](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) legacy) finestra di dialogo [Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [con condizioni nei flussi di lavoro](https://go.microsoft.com/fwlink?LinkID=65009)