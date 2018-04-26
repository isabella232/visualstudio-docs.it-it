---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Editor condizione della regola (Legacy)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f723894f175cbf031c3a2ac61ed9eaec8e1c94f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Finestra di dialogo Editor condizione della regola (legacy)

Questo argomento viene descritto come utilizzare il **Editor condizione della regola** nella finestra di dialogo di progettazione del flusso di lavoro Windows legacy. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando è necessario avere come destinazione .NET Framework versione 3.5 o la WinFX.

Creare e modificare regole dichiarative utilizzando il **Editor condizione della regola** la finestra di dialogo. Queste condizioni della regola sono esposte come proprietà nelle attività predefinite di Windows Workflow Foundation seguenti:

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

Si accede di **Editor condizione della regola** la finestra di dialogo utilizzando il [selezionare la finestra di dialogo condizione (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Editor condizione della regola** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Condizione:**|Immettere l'espressione per la condizione della regola.|
|**OK**|Fare clic per salvare la condizione della regola.|

## <a name="entering-condition-expressions"></a>Immissione delle espressioni della condizione.

Le espressioni della condizione vengono immesse in formato testo. È possibile digitare **questo.** Nell'editor per fare riferimento a campi, proprietà e metodi usati nel flusso di lavoro, tramite un menu come IntelliSense. In alternativa, è possibile digitare direttamente il nome di un membro del flusso di lavoro. È possibile aggiungere operatori logici alla condizione, ad esempio E, O e NON. È anche possibile aggiungere predicati. Un predicato è composto da un operatore binario e due operandi. Gli operatori binari supportati sono **==**, **>**, **\<**, **>=**, e **<=**. Gli operandi supportati sono membri pubblici ai quali è stato assegnato un valore costante, una funzione aritmetica e un ambito.

È possibile specificare il tipo per il confronto, ed è possibile confrontare a **null** o una stringa vuota. È possibile effettuare chiamate annidate ai membri su una variabile contenente un tipo complesso, ad esempio, `this.Address.State == "WA"`.

L'Editor della condizione della regola supporta gli operatori seguenti:

-   operatori relazionali: ==, =, !=

-   Gli operatori di confronto: <, \<=, >, > =

-   Operatori aritmetici: +, -, \*, /, MOD

-   Operatori logici: E, & &, OR, &#124; &#124;, NOT,!

-   Operatori bit per bit: &,&#124;

La precedenza di operatori dell’espressione segue le regole di precedenza dell’operatore C#.

L'Editor della condizione della regola supporta le espressioni numeriche seguenti:

i == 1D dà come risultato 1.0.

i == 1E1 dà come risultato 10.0.

i == 1L dà come risultato un numero intero lungo

i == 1M dà come risultato un numero decimale

i == 1F dà come risultato un numero singolo

i == 1U dà come risultato un unsigned int

Per ulteriori informazioni sulle condizioni, vedere [utilizzo delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Vedere anche

- [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)
- [Attività WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)
- [Finestra di dialogo Seleziona condizione (legacy)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [Utilizzo delle condizioni nei flussi di lavoro](http://go.microsoft.com/fwlink?LinkID=65009)
- [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)