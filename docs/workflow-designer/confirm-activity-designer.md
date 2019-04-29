---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner Confirm
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8418faf7fb4eb55a0b20a33aaaa2909e07ff7a78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949855"
---
# <a name="confirm-activity-designer"></a>ActivityDesigner Confirm

Il **Confirm** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Confirm> attività.

## <a name="the-confirm-activity"></a>Attività Confirm
 L'attività <xref:System.Activities.Statements.Confirm> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Confirm> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Utilizzo dell'ActivityDesigner Confirm
 Il **Confirm** ActivityDesigner è reperibile nella **transazione** categoria del **della casella degli strumenti**, accessibile facendo clic la **della casella degli strumenti**scheda sul lato sinistro della finestra di progettazione del flusso di lavoro. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

 Il **Confirm** ActivityDesigner può essere trascinato dalle **della casella degli strumenti** e rilasciate sull'area di progettazione del flusso di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.Confirm> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Confirm. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione del **Confirm** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.

### <a name="the-confirm-properties"></a>Proprietà di Confirm
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Confirm> e ne viene descritta la modalità di uso nella finestra di progettazione. Il <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà o nell'area di progettazione del flusso di lavoro, ma il <xref:System.Activities.Statements.Confirm.Target%2A> proprietà deve essere modificata nella griglia delle proprietà.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. L'impostazione predefinita è Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Vedere anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)