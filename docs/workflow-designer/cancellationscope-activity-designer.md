---
title: ActivityDesigner CancellationScope
description: Informazioni su come usare l'ActivityDesigner CancellationScope in Progettazione flussi di lavoro creare e configurare un'attività CancellationScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 91eb31444a56d68f062f7909d9fb5de13d3f496d
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963366"
---
# <a name="cancellationscope-activity-designer"></a>ActivityDesigner CancellationScope

**L'ActivityDesigner CancellationScope** viene usato per creare e configurare <xref:System.Activities.Statements.CancellationScope> un'attività.

## <a name="the-cancellationscope-activity"></a>Attività CancellationScope

L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilizzo dell'ActivityDesigner CancellationScope

**L'ActivityDesigner CancellationScope** è disponibile nella categoria **Transazione** della Casella **degli strumenti**. Per aprire **casella degli** strumenti , selezionare la **scheda Casella** degli strumenti del Progettazione flussi di lavoro. In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

**L'ActivityDesigner CancellationScope** può  essere trascinato dalla casella degli strumenti e rilasciato sulla superficie Progettazione flussi di lavoro ogni volta che vengono inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione **dell'ActivityDesigner CancellationScope** crea <xref:System.Activities.Statements.CancellationScope> un'attività con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito CancellationScope. Modificare il <xref:System.Activities.Activity.DisplayName%2A> valore nell'intestazione dell'ActivityDesigner **CancellationScope.** È anche possibile modificarlo nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-cancellationscope-properties"></a>Proprietà di CancellationScope

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. La proprietà può essere modificata nella griglia delle proprietà, ma le altre proprietà devono essere modificate <xref:System.Activities.Activity.DisplayName%2A> Progettazione flussi di lavoro superficie.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>. Il valore predefinito è CancellationScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Vero|Specifica l'attività per la quale viene fornita la logica di annullamento. Per aggiungere <xref:System.Activities.Statements.CancellationScope.Body%2A> l'attività,  rilasciare un'attività dalla casella degli strumenti **nella casella Corpo** dell'ActivityDesigner **CancellationScope.** Aggiungere il testo del suggerimento "Drop Activity Here" (Rilascia attività qui).|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Vero|Specifica l'attività eseguita in caso di annullamento. Per aggiungere <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> l'attività,  rilasciare un'attività dalla casella degli strumenti nella **casella CancellationHandler** dell'ActivityDesigner **CancellationScope.** Aggiungere il testo del suggerimento "Drop Activity Here" (Rilascia attività qui).|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
