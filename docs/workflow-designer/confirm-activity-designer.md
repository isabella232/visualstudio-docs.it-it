---
title: ActivityDesigner Progettazione flussi di lavoro-Confirm
description: Informazioni sull'ActivityDesigner Confirm e sul modo in cui è possibile utilizzare questa finestra di progettazione per creare e configurare un'attività Confirm.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4928dcd7a9e1b83ba797614545315022d0f36ac3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438152"
---
# <a name="confirm-activity-designer"></a>ActivityDesigner Confirm

L'ActivityDesigner **Confirm** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Confirm> attività.

## <a name="the-confirm-activity"></a>Attività Confirm
 L'attività <xref:System.Activities.Statements.Confirm> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Confirm> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Utilizzo dell'ActivityDesigner Confirm
 L'ActivityDesigner **Confirm** è disponibile nella categoria **Transaction** della **casella degli strumenti** , a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

 È possibile trascinare l'ActivityDesigner **Confirm** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.Confirm> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Confirm. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Confirm** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-confirm-properties"></a>Proprietà di Confirm
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Confirm> e ne viene descritta la modalità di uso nella finestra di progettazione. La <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà o nell'area di progettazione flussi di lavoro, ma la <xref:System.Activities.Statements.Confirm.Target%2A> proprietà deve essere modificata nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. L'impostazione predefinita è Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Vero|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)