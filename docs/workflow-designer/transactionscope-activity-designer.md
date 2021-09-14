---
title: Progettazione flussi di lavoro - ActivityDesigner TransactionScope
description: Informazioni su come usare l'ActivityDesigner TransactionScope per creare e configurare un'attività TransactionScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d3d84514690c4f2a00caea3b88946ffbd4da7cbc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710562"
---
# <a name="transactionscope-activity-designer"></a>ActivityDesigner TransactionScope

**L'ActivityDesigner TransactionScope** viene usato per creare e configurare <xref:System.Activities.Statements.TransactionScope> un'attività.

## <a name="the-transactionscope-activity"></a>Attività TransactionScope

L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta. Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.

### <a name="using-the-transactionscope-activity-designer"></a>Utilizzo dell'ActivityDesigner TransactionScope

Accedere **all'ActivityDesigner TransactionScope** nella **categoria Transazione** della Casella **degli strumenti**. **L'ActivityDesigner TransactionScope** può essere  trascinato dalla casella degli strumenti e rilasciato sulla superficie di Progettazione flussi di lavoro ogni volta che vengono in genere inserite attività, ad esempio all'interno di <xref:System.Activities.Statements.Sequence> un oggetto . In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **TransactionScope** o nella **casella DisplayName** della griglia delle proprietà.

### <a name="the-transactionscope-properties"></a>Proprietà di TransactionScope

Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> e ne viene descritta la modalità di uso nella finestra di progettazione. Le <xref:System.Activities.Activity.DisplayName%2A> proprietà e possono essere modificate in Progettazione flussi di lavoro <xref:System.Activities.Statements.TransactionScope.Body%2A> superficie. Le altre proprietà devono invece essere modificate nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>. Il valore predefinito è TransactionScope. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|Vero|Consente di specificare l'attività da eseguire in un'unica transazione. Per aggiungere <xref:System.Activities.Statements.TransactionScope.Body%2A> l'attività, rilasciare un'attività  dalla casella degli strumenti nella casella Corpo  dell'ActivityDesigner **TransactionScope** con il testo del suggerimento "Drop activity here".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|Vero|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|Falso|Consente di specificare l'intervallo di tempo (nel formato 00:00:00, che indica ore:minuti:secondi) disponibile per il completamento della transazione. Il valore predefinito è 1 minuto (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|Vero|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|

## <a name="see-also"></a>Vedi anche

- [Transazione](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensare](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
