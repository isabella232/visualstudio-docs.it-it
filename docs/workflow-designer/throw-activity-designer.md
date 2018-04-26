---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Throw
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb94ad17b78b1264129b8a5ba00a964edbd2f2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="throw-activity-designer"></a>ActivityDesigner Throw

Il **generare** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Throw> attività.

## <a name="the-throw-activity"></a>Attività Throw
 L'attività <xref:System.Activities.Statements.Throw> genera un'eccezione.

### <a name="using-the-throw-activity-designer"></a>Utilizzo dell'ActivityDesigner Throw
 Il **Throw** ActivityDesigner è reperibile nella **Error Handling** categoria del **casella degli strumenti**, accessibile facendo clic il **della casella degli strumenti**scheda sul lato sinistro della finestra di progettazione del flusso di lavoro (in alternativa, selezionare **sulla barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **Throw** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Throw> attività con valore predefinito è **DisplayName** throw. Il <xref:System.Activities.Activity.DisplayName%2A> possibile modificare il valore nell'intestazione del **generare** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà. La proprietà <xref:System.Activities.Statements.Throw.Exception%2A> deve essere modificata nella griglia delle proprietà.

### <a name="the-throw-properties"></a>Proprietà di Throw
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Throw> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Throw>. Il valore predefinito è Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Eccezione da generare. Questa eccezione deve derivare da <xref:System.Exception>. Per specificare l'eccezione, digitare un'espressione Visual Basic nella griglia delle proprietà.|

## <a name="see-also"></a>Vedere anche

- [Raccolta](../workflow-designer/collection-activity-designers.md)
- [rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Activity Designer Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)