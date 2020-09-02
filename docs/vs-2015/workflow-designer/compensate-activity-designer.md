---
title: ActivityDesigner Compensate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656985"
---
# <a name="compensate-activity-designer"></a>ActivityDesigner Compensate
L'ActivityDesigner **compensate** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Compensate> attività.

## <a name="the-compensate-activity"></a>Attività Compensate
 L'attività <xref:System.Activities.Statements.Compensate> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>. Se l'attività <xref:System.Activities.Statements.Compensate> non viene usata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Compensate.Target%2A>.

 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.

### <a name="using-the-compensate-activity-designer"></a>Utilizzo dell'ActivityDesigner Compensate
 L'ActivityDesigner **compensate** è disponibile nella categoria **transazione** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** sul lato sinistro del. in [!INCLUDE[wfd2](../includes/wfd2-md.md)] alternativa, scegliere **barra degli** strumenti dal menu **Visualizza** oppure premere CTRL + ALT + X.

 È possibile trascinare l'ActivityDesigner **compensate** dalla **casella degli strumenti** e rilasciarlo nell' [!INCLUDE[wfd2](../includes/wfd2-md.md)] area in cui vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . In questo modo viene creata un'attività <xref:System.Activities.Statements.Compensate> con la  proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Compensate. Il <xref:System.Activities.Activity.DisplayName%2A> valore può essere modificato nell'intestazione dell'ActivityDesigner **compensate** oppure nella casella **DisplayName** della griglia delle proprietà.

### <a name="the-compensate-properties"></a>Proprietà di Compensate
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> e ne viene descritta la modalità di uso nella finestra di progettazione. La proprietà <xref:System.Activities.Activity.DisplayName%2A> può essere modificata nella griglia delle proprietà o nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)], mentre la proprietà <xref:System.Activities.Statements.Compensate.Target%2A> deve essere modificata nella griglia delle proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Compensate>. L'impostazione predefinita è Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|Vero|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Vedere anche
 [Finestra di progettazione attività compensata](../workflow-designer/compensate-activity-designer.md) [Transaction](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Confirm](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)