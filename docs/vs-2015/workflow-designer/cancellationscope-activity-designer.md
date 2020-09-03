---
title: ActivityDesigner ActivityDesigner CancellationScope t | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659173"
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope
L'ActivityDesigner **ActivityDesigner CancellationScope t** viene usato per creare e configurare un' <xref:System.Activities.Statements.CancellationScope> attività.

## <a name="the-cancellationscope-activity"></a>Attività CancellationScope
 L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope
 L'ActivityDesigner **ActivityDesigner CancellationScope t** è disponibile nella categoria **transazione** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** di. [!INCLUDE[wfd2](../includes/wfd2-md.md)] in alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **ActivityDesigner CancellationScope t** dalla **casella degli strumenti** e rilasciarlo nell'area in cui [!INCLUDE[wfd2](../includes/wfd2-md.md)] vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.CancellationScope> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito CancellationScope. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **ActivityDesigner CancellationScope t** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. È possibile modificare la proprietà <xref:System.Activities.Activity.DisplayName%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Vero|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere l' <xref:System.Activities.Statements.CancellationScope.Body%2A> attività, rilasciare un'attività dalla casella **degli strumenti** nella casella **corpo** dell'ActivityDesigner **ActivityDesigner CancellationScope t** con il testo del suggerimento "drop Activity here".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Vero|Specifica l'attività eseguita in caso di annullamento. Per aggiungere l' <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> attività, rilasciare un'attività dalla casella **degli strumenti** nella casella **CancellationHandler** nell'ActivityDesigner **ActivityDesigner CancellationScope t** con il testo del suggerimento "drop Activity here".|

## <a name="see-also"></a>Vedere anche
 [Transazione](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) [conferma](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)