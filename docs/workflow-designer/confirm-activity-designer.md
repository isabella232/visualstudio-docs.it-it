---
title: Progettazione flussi di lavoro - Conferma ActivityDesigner
description: Informazioni sull'ActivityDesigner Confirm e su come usare questa finestra di progettazione per creare e configurare un'attività Confirm.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 017a89d2e68e3d466f7625c8dbb2312d450f888c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633707"
---
# <a name="confirm-activity-designer"></a>ActivityDesigner Confirm

L'ActivityDesigner **Confirm** viene usato per creare e configurare <xref:System.Activities.Statements.Confirm> un'attività.

## <a name="the-confirm-activity"></a>Attività Confirm
 L'attività <xref:System.Activities.Statements.Confirm> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Confirm> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-confirm-activity-designer"></a>Utilizzo dell'ActivityDesigner Confirm
 L'ActivityDesigner Confirm è  disponibile nella categoria Transazione della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda  **Casella** degli strumenti sul lato sinistro del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

 L'ActivityDesigner **Confirm** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.Confirm> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Confirm. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **Confirm** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-confirm-properties"></a>Proprietà di Confirm
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Confirm> e ne viene descritta la modalità di uso nella finestra di progettazione. La proprietà può essere modificata nella griglia delle proprietà o Progettazione flussi di lavoro, ma la proprietà deve essere modificata <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Statements.Confirm.Target%2A> nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. L'impostazione predefinita è Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Vero|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)