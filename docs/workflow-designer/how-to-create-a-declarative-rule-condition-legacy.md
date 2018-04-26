---
title: 'Finestra di progettazione del flusso di lavoro - procedura: creare una condizione della regola dichiarativa (Legacy)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43b359040256788db240274f43f706b41f01d021
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procedura: creare una condizione della regola dichiarativa (legacy)

In questo argomento viene descritto come dichiarare una condizione della regola usando Progettazione flussi di lavoro Windows legacy che fa riferimento a .NET Framework versione 3.5 o la WinFX.

Restituisce un'istruzione di condizione **True** o **False**. Una condizione della regola dichiarativa è un'istruzione di condizione che viene creata utilizzando il [finestra di dialogo Editor regole condizione (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e archiviati in formato XML con il flusso di lavoro. Può includere predicati che confrontano lo stato del flusso di lavoro con l'algebra booleana che combina più predicati.

Le condizioni di regole dichiarative vengono usate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

## <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Per creare una condizione di regole dichiarative usando l’Editor della condizione della regola

1.  L'attività **proprietà** finestra, fare clic su di **condizione** proprietà o **UntilCondition** proprietà, a seconda dell'attività.

2.  Selezionare **condizione della regola dichiarativa** dall'elenco per la proprietà.

3.  Espandere il **condizione** o **UntilCondition** proprietà.

4.  Fare clic su di **ConditionName** proprietà.

5.  Fare clic su di **ConditionName** i puntini di sospensione **[…]**  per aprire la **Seleziona condizione** la finestra di dialogo.

6.  Fare clic su **nuova condizione** per aprire la **Editor condizione della regola** la finestra di dialogo.

7.  Digitare l'espressione per la condizione di **condizione** casella di testo.

     Per informazioni su come creare espressioni di condizione, vedere [finestra di dialogo Editor regole condizione (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8.  Dopo aver creato l'espressione della condizione, fare clic su **OK** per chiudere la finestra di dialogo e creare la condizione della regola con un nome assegnato.

     Il **Seleziona condizione** verrà visualizzata la finestra di dialogo.

     Per informazioni sull'utilizzo di **Seleziona condizione** la finestra di dialogo, vedere [selezionare la finestra di dialogo condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Vedere anche

- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)
- [Utilizzo di ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)
- [Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)
- [Utilizzo dell'attività di replica](http://go.microsoft.com/fwlink?LinkID=65080)
- [Utilizzo di While attività](http://go.microsoft.com/fwlink?LinkID=65091)
- [Finestra di dialogo Editor condizione della regola (legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [Finestra di dialogo Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Utilizzo delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)