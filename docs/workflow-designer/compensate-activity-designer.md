---
title: Progettazione flussi di lavoro - ActivityDesigner Compensate
description: Informazioni sull'ActivityDesigner Compensate e su come è possibile usare l'ActivityDesigner Compensate per creare e configurare un'attività Compensate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: cf967b079fbd499a3e3cf244c5c6dd692aa01e363b7e69db10f7299ca3422448
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121383937"
---
# <a name="compensate-activity-designer"></a>ActivityDesigner Compensate

**L'ActivityDesigner Compensate** viene usato per creare e configurare <xref:System.Activities.Statements.Compensate> un'attività.

## <a name="the-compensate-activity"></a>Attività Compensate

L'attività <xref:System.Activities.Statements.Compensate> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Compensate> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Compensate.Target%2A>.

L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-compensate-activity-designer"></a>Utilizzo dell'ActivityDesigner Compensate

**L'ActivityDesigner Compensate** è disponibile nella **categoria Transazione** della Casella **degli strumenti**. Per aprire **La casella degli** strumenti , selezionare la scheda Casella degli strumenti sul lato sinistro del Progettazione flussi di lavoro.  In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

**L'ActivityDesigner Compensate** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione dell'ActivityDesigner crea <xref:System.Activities.Statements.Compensate> un'attività con <xref:System.Activities.Activity.DisplayName%2A> l'impostazione predefinita Compensate. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Compensate** o nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-compensate-properties"></a>Proprietà di Compensate

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. La <xref:System.Activities.Activity.DisplayName%2A> proprietà può essere modificata nella griglia delle proprietà o nella Progettazione flussi di lavoro proprietà. Modificare la <xref:System.Activities.Statements.Compensate.Target%2A> proprietà nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Compensate>. L'impostazione predefinita è Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Vero|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Activity Designer Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)