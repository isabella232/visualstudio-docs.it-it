---
title: ActivityDesigner Compensate Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5332b6d9ec087f4e1b127d93563dc0f2fe5fdd15
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876151"
---
# <a name="compensate-activity-designer"></a>ActivityDesigner Compensate

L'ActivityDesigner **compensate** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Compensate> attività.

## <a name="the-compensate-activity"></a>Attività Compensate

L'attività <xref:System.Activities.Statements.Compensate> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Compensate> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Compensate.Target%2A>.

L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-compensate-activity-designer"></a>Utilizzo dell'ActivityDesigner Compensate

L'ActivityDesigner **compensate** è reperibile nella categoria **transazione** della **casella degli strumenti**. Per aprire la **casella degli strumenti**, selezionare la scheda **casella degli strumenti** sul lato sinistro del progettazione flussi di lavoro. In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

È possibile trascinare l'ActivityDesigner **compensate** dalla **casella degli strumenti** e rilasciarlo nell'area Progettazione flussi di lavoro ogni volta che vengono posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner, viene creata un' <xref:System.Activities.Statements.Compensate> attività con il valore predefinito <xref:System.Activities.Activity.DisplayName%2A> compensate. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **compensate** oppure nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-compensate-properties"></a>Proprietà di Compensate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. La <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà o nell'area Progettazione flussi di lavoro. Modificare la <xref:System.Activities.Statements.Compensate.Target%2A> proprietà nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Compensate>. L'impostazione predefinita è Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Vero|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Activity Designer Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confermare](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)