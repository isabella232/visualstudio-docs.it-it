---
title: Activity Designer CancellationScope | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 125e9fd934ce40d2a6633daa62b817628306daa3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229892"
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope
Il **CancellationScope** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.CancellationScope> attività.  
  
## <a name="the-cancellationscope-activity"></a>Attività CancellationScope  
 L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope  
 Il **CancellationScope** ActivityDesigner è reperibile nel **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**  scheda della finestra di [!INCLUDE[wfd2](../includes/wfd2-md.md)] (in alternativa, selezionare **sulla barra degli strumenti** dal **visualizzazione** menu oppure premere CTRL + ALT + X.)  
  
 Il **CancellationScope** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.CancellationScope> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito CancellationScope. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **CancellationScope** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. È possibile modificare la proprietà <xref:System.Activities.Activity.DisplayName%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere il <xref:System.Activities.Statements.CancellationScope.Body%2A> attività, rilasciare un'attività dal **della casella degli strumenti** nel **corpo** casella il **CancellationScope** ActivityDesigner con testo di suggerimento "Drop Attività".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Specifica l'attività eseguita in caso di annullamento. Per aggiungere il <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> attività, rilasciare un'attività dal **della casella degli strumenti** nel **CancellationHandler** casella il **CancellationScope** ActivityDesigner con hint testo "Rilasciare l'attività".|  
  
## <a name="see-also"></a>Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensare](../workflow-designer/compensate-activity-designer.md)   
 [Confermare](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)