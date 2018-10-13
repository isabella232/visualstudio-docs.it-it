---
title: 'Procedura: creare un Set di regole di attività PolicyActivity (Legacy) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7ab49957d830bf558a9dddf55cdc5e8c2f3f75d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194623"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procedura: creare un set di regole per l'attività PolicyActivity (legacy)
In questo argomento viene descritto come creare un set di regole per PolicyActivity usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Dopo avere trascinato un **criterio** elemento di attività dalle **della casella degli strumenti** all'area di progettazione del flusso di lavoro, è consigliabile selezionare una regola esistente o creare una nuovo set di regole per il [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) attività. Si seleziona una regola esistente impostata usando il [selezionare Imposta finestra di dialogo regola (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) e crei i set di regole mediante il [impostare Editor finestra di dialogo regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  È possibile aprire il [impostare Editor finestra di dialogo regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) finestra di dialogo direttamente facendo doppio clic su un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) attività nell'area di progettazione del flusso di lavoro.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Per selezionare o creare un insieme di regole per un'attività di Policy  
  
1.  Fare doppio clic sui [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)e quindi fare clic su **delle proprietà** per aprire il **proprietà** finestra.  
  
2.  Scegliere il **RuleSetReference** proprietà.  
  
3.  Eseguire una delle operazioni seguenti:  
  
    -   Scegliere il **RuleSetReference** puntini di sospensione **[...]** , quindi selezionare una set di regole esistente di [selezionare Imposta finestra di dialogo regola (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Andare al passaggio 10.  
  
         -oppure-  
  
    -   Digitare il nome da assegnare al set di regole. Scegliere il **RuleSetReference** puntini di sospensione **[...]** , quindi selezionare **modificare** nel [selezionare Imposta finestra di dialogo regola (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         oppure  
  
    -   Digitare il nome da assegnare al set di regole. Espandere la **RuleSetReference** proprietà e selezionare i puntini di sospensione **[...]**  nella **RuleSet Definition** proprietà.  
  
         Il [impostare Editor finestra di dialogo regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) apre.  
  
4.  Nel [impostare Editor finestra di dialogo regola (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), fare clic su **Add Rule** per aggiungere una nuova regola per il set di regole.  
  
5.  Immettere il **Name**, **priorità**, e **rivalutazione** proprietà, oppure mantenere i valori predefiniti.  
  
6.  Immettere il testo per il **condizione**.  
  
7.  Immettere il testo per il **azioni Then** e il **azioni Else**.  
  
8.  Fare clic su **Aggiungi regola** nuovo per aggiungere un'altra regola.  
  
9. Al termine, fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Finestra di dialogo Set di regola selezionare (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Set di regole (Legacy) finestra di dialogo Editor](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Utilizzo dell'attività Policy](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)