---
title: 'Procedura: creare un set di regole PolicyActivity (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c200c7db90f3cad12c1188af88f4651d2f2d44c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663384"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procedura: creare un set di regole per l'attività PolicyActivity (legacy)
In questo argomento viene descritto come creare un set di regole per PolicyActivity usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dopo avere trascinato un elemento dell'attività **policy** dalla **casella degli strumenti** all'area di progettazione del flusso di lavoro, è necessario selezionare una regola esistente o creare un nuovo set di regole per l'attività [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) . Per selezionare un set di regole esistente, utilizzare la finestra di [dialogo Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e creare set di regole utilizzando la finestra di [dialogo Editor set di regole (legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> È possibile aprire la finestra di dialogo [Editor set di regole (legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) direttamente facendo doppio clic su un'attività [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) che si trova sull'area di progettazione del flusso di lavoro.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Per selezionare o creare un insieme di regole per un'attività di Policy

1. Fare clic con il pulsante destro del mouse su [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)e quindi scegliere **Proprietà** per aprire la finestra **proprietà** .

2. Fare clic sulla proprietà **RuleSetReference** .

3. Effettuare una delle operazioni riportate di seguito:

    - Fare clic sui puntini di sospensione **[...]** di **RuleSetReference** e quindi selezionare un set di regole esistente nella finestra di [dialogo Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Andare al passaggio 10.

         oppure

    - Digitare il nome da assegnare al set di regole. Fare clic sui puntini di sospensione **[...]** di **RuleSetReference** e quindi selezionare **modifica** nella finestra di [dialogo Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         oppure

    - Digitare il nome da assegnare al set di regole. Espandere la proprietà **RuleSetReference** e selezionare i puntini di sospensione **[...]** nella proprietà di **definizione di RuleSet** .

         Verrà visualizzata la finestra di [dialogo Editor set di regole (legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) .

4. Nella finestra di [dialogo Editor set di regole (legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)fare clic su **Aggiungi regola** per aggiungere una nuova regola al set di regole.

5. Immettere le proprietà **nome**, **priorità**e **rivalutazione** oppure Mantieni i valori predefiniti.

6. Immettere il testo per la **condizione**.

7. Immettere il testo per le azioni **then** e **else**.

8. Fare di nuovo clic su **Aggiungi regola** per aggiungere un'altra regola.

9. Al termine, fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) finestra di dialogo [Seleziona set di regole (legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) finestra di dialogo [Editor set di regole (legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [utilizzando le](http://go.microsoft.com/fwlink?LinkID=65004) attività [del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) attività criterio