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
ms.openlocfilehash: d3a15aad987e46edb58da3560828c70571df2227
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663421"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procedura: creare una condizione della regola dichiarativa (legacy)
In questo argomento viene descritto come dichiarare una condizione della regola usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un'istruzione Condition restituisce **true** o **false**. Una condizione della regola dichiarativa è un'istruzione della condizione creata tramite la finestra di [dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e archiviata come XML con il flusso di lavoro. Può includere predicati che confrontano lo stato del flusso di lavoro con l'algebra booleana che combina più predicati.

 Le condizioni di regole dichiarative vengono usate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:

- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

- [Dell'WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

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
 [Attività del flusso di lavoro legacy che](../workflow-designer/legacy-workflow-activities.md) [usano ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066) [usando l'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075) [usando l'attività Replicator](http://go.microsoft.com/fwlink?LinkID=65080) [usando la finestra di](http://go.microsoft.com/fwlink?LinkID=65091) [dialogo Editor condizione della regola attività (legacy) ](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)Finestra di [dialogo Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [utilizzo di condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)