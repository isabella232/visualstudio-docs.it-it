---
title: ActivityDesigner Confirm | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656967"
---
# <a name="confirm-activity-designer"></a>ActivityDesigner Confirm
L'ActivityDesigner **Confirm** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Confirm>.

## <a name="the-confirm-activity"></a>Attività Confirm
 L'attività <xref:System.Activities.Statements.Confirm> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Confirm> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Utilizzo dell'ActivityDesigner Confirm
 L'ActivityDesigner **Confirm** è disponibile nella categoria **Transaction** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del [!INCLUDE[wfd2](../includes/wfd2-md.md)]. in alternativa, selezionare **barra degli** strumenti dalla **vista** menu o CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **Confirm** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.Confirm> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Confirm. Il valore <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **Confirm** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-confirm-properties"></a>Proprietà di Confirm
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Confirm> e ne viene descritta la modalità di uso nella finestra di progettazione. La proprietà <xref:System.Activities.Activity.DisplayName%2A> può essere modificata nella griglia delle proprietà o nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)], mentre la proprietà <xref:System.Activities.Statements.Confirm.Target%2A> deve essere modificata nella griglia delle proprietà.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. L'impostazione predefinita è Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Vedere anche
 [Transazione](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)