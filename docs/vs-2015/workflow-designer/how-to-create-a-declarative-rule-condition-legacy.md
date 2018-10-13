---
title: 'Procedura: creare una condizione della regola dichiarativa (Legacy) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2508404840db81f03ba4865a3e5d5af91e5c653b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187411"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procedura: creare una condizione della regola dichiarativa (legacy)
In questo argomento viene descritto come dichiarare una condizione della regola usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Un'istruzione di condizione restituisce **True** oppure **False**. Una condizione della regola dichiarativa è un'istruzione della condizione che viene creata usando il [finestra di dialogo Editor condizione regola (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) e archiviata in formato XML con il flusso di lavoro. Può includere predicati che confrontano lo stato del flusso di lavoro con l'algebra booleana che combina più predicati.  
  
 Le condizioni di regole dichiarative vengono usate nelle attività predefinite di Windows Workflow Foundation di seguito riportate:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [Attività ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Per creare una condizione di regole dichiarative usando l’Editor della condizione della regola  
  
1.  Dell'attività **delle proprietà** finestra, fare clic sui **condizione** proprietà o **UntilCondition** proprietà, a seconda dell'attività.  
  
2.  Selezionare **condizione della regola dichiarativa** dall'elenco per la proprietà.  
  
3.  Espandere la **Condition** oppure **UntilCondition** proprietà.  
  
4.  Scegliere il **ConditionName** proprietà.  
  
5.  Scegliere il **ConditionName** puntini di sospensione **[...]**  per aprire la **Seleziona condizione** nella finestra di dialogo.  
  
6.  Fare clic su **nuova condizione** per aprire il **Editor condizione della regola** nella finestra di dialogo.  
  
7.  Digitare l'espressione per la condizione nel **condizione** casella di testo.  
  
     Per informazioni su come creare espressioni della condizione, vedere [finestra di dialogo Editor condizione regola (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Quando si è finito di creare l'espressione della condizione, fare clic su **OK** per chiudere la finestra di dialogo e creare la condizione della regola con un nome assegnato.  
  
     Il **Seleziona condizione** verrà visualizzata la finestra di dialogo.  
  
     Per informazioni su come usare il **Seleziona condizione** finestra di dialogo, vedere [seleziona finestra di dialogo condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Utilizzo dell'attività ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Utilizzo dell'attività IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Utilizzo del ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Utilizzo di While attività](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Finestra di dialogo Editor condizione della regola (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Finestra di dialogo Seleziona condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Uso delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)