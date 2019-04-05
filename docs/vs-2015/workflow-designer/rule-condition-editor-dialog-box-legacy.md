---
title: Finestra di dialogo Editor condizione della regola (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8237c8e29007d010cd99e4323bf8e88a23b7e9fb
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "58955931"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Finestra di dialogo Editor condizione della regola (legacy)
Questo argomento viene descritto come usare il **Editor condizione della regola** nella finestra di dialogo legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Creare e modificare condizioni della regola dichiarativa tramite le **Editor condizione della regola** nella finestra di dialogo. Queste condizioni della regola sono esposte come proprietà nelle attività predefinite di Windows Workflow Foundation seguenti:  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
  Si accede il **Editor condizione della regola** finestra di dialogo tramite il [seleziona finestra di dialogo condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
  La tabella seguente descrive gli elementi dell'interfaccia utente di **Editor condizione della regola** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Condizione:**|Immettere l'espressione per la condizione della regola.|  
|**OK**|Fare clic per salvare la condizione della regola.|  
  
## <a name="entering-condition-expressions"></a>Immissione delle espressioni della condizione.  
 Le espressioni della condizione vengono immesse in formato testo. È possibile digitare **questo.** Nell'editor per fare riferimento a campi, proprietà e metodi usati nel flusso di lavoro, tramite un menu come IntelliSense. In alternativa, è possibile digitare direttamente il nome di un membro del flusso di lavoro. È possibile aggiungere operatori logici alla condizione, ad esempio E, O e NON. È anche possibile aggiungere predicati. Un predicato è composto da un operatore binario e due operandi. Gli operatori binari supportati sono **==**, **>**, **\<**, **>=**, e **<=**. Gli operandi supportati sono membri pubblici ai quali è stato assegnato un valore costante, una funzione aritmetica e un ambito.  
  
 È possibile specificare il tipo per il confronto, ed è possibile confrontare con **null** o una stringa vuota. È possibile effettuare chiamate annidate ai membri su una variabile contenente un tipo complesso, ad esempio, `this.Address.State == "WA"`.  
  
 L'Editor della condizione della regola supporta gli operatori seguenti:  
  
- operatori relazionali: ==, =, !=  
  
- Gli operatori di confronto: <, \<=, >, > =  
  
- Operatori aritmetici: +, - , *, /, MOD  
  
- Operatori logici: AND, &&, OR, &#124;&#124;, NOT, !  
  
- Operatori bit per bit: &,&#124;  
  
  La precedenza di operatori dell’espressione segue le regole di precedenza dell’operatore C#.  
  
  L'Editor della condizione della regola supporta le espressioni numeriche seguenti:  
  
  i == 1D dà come risultato 1.0.  
  
  i == 1E1 dà come risultato 10.0.  
  
  i == 1L dà come risultato un numero intero lungo  
  
  i == 1M dà come risultato un numero decimale  
  
  i == 1F dà come risultato un numero singolo  
  
  i == 1U dà come risultato un unsigned int  
  
  Per altre informazioni sulle condizioni, vedere [utilizzo delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## <a name="see-also"></a>Vedere anche  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Finestra di dialogo Seleziona condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Uso delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)