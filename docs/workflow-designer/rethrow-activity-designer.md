---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Rethrow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d441724afa1cf481bc15e2a43e6ec744a951187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="rethrow-activity-designer"></a>ActivityDesigner Rethrow

Il **Rethrow** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Rethrow> attività.

## <a name="the-rethrow-activity"></a>Attività Rethrow
 L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente. Questa attività può essere usata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Utilizzo dell'ActivityDesigner ReThrow
 Il **Rethrow** ActivityDesigner è reperibile nella **Error Handling** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**scheda sul lato sinistro della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu o premere CTRL + ALT + X.)

 Il **Rethrow** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Rethrow> attività con valore predefinito è **DisplayName** throw. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **Rethrow** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-rethrow-properties"></a>Proprietà di Rethrow
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Rethrow> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Rethrow>. Il valore predefinito è Rethrow.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)