---
title: Activity Designer CompensableActivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f11743e0027866fd45687f716f1989e98020c68e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968239"
---
# <a name="compensableactivity-activity-designer"></a>ActivityDesigner CompensableActivity
Il **CompensableActivity** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CompensableActivity> attività.  
  
## <a name="the-compensableactivity-activity"></a>Attività CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Utilizzo dell'ActivityDesigner CompensableActivity  
 Il **CompensableActivity** ActivityDesigner è reperibile nel **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**  sul lato sinistro della scheda il [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **CompensableActivity** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.CompensableActivity> con un elemento <xref:System.Activities.Activity.DisplayName%2A> predefinito di CompensableActivity. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **CompensableActivity** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-compensableactivity-properties"></a>Proprietà di CompensableActivity  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di uso nella finestra di progettazione. È possibile modificare le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>. Il valore predefinito è CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>. Questa proprietà deve essere modificata nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma. Per aggiungere il <xref:System.Activities.Statements.CompensableActivity.Body%2A> attività, rilasciare un'attività dal **della casella degli strumenti** nel **corpo** casella il **CompensableActivity** ActivityDesigner con testo di suggerimento "Drop attività".|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l'attività, rilasciarne relativa finestra di progettazione dal **casella degli strumenti** nel **CancellationHandler** nella casella il **CompensableActivity** ActivityDesigner con testo di suggerimento "Drop Attività".|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, rilasciarne relativi ActivityDesigner dal **casella degli strumenti** nel **CompensationHandler** nella casella il **CompensableActivity** ActivityDesigner con testo di suggerimento " Rilascia attività qui".|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>. È possibile richiamare questo gestore in modo esplicito usando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, rilasciarne relativi ActivityDesigner dal **casella degli strumenti** nel **ConfirmationHandler** nella casella il **CompensableActivity** ActivityDesigner con testo di suggerimento " Rilascia attività qui".|  
  
## <a name="see-also"></a>Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Compensare](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)