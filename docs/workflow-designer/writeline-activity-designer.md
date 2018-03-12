---
title: ActivityDesigner WriteLine | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8596aa9f00e75ec31a29042473d728310027bc36
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="writeline-activity-designer"></a>ActivityDesigner WriteLine
Il **WriteLine** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.WriteLine> attività.

## <a name="the-writeline-activity"></a>Attività WriteLine
 L'attività <xref:System.Activities.Statements.WriteLine> scrive il testo in un oggetto <xref:System.IO.TextWriter> specificato. Se non è specificato alcun oggetto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> scrive il testo sulla console.

### <a name="using-the-writeline-activity-designer"></a>Utilizzo dell'ActivityDesigner WriteLine
 Il **WriteLine** ActivityDesigner è reperibile nel **primitive** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda della finestra il [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (in alternativa, selezionare **barra degli strumenti** dal **vista** menu oppure premere CTRL + ALT + X.)

 Il **WriteLine** da, è possibile trascinare l'ActivityDesigner di **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] area ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività <xref:System.Activities.Statements.WriteLine> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito WriteLine. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **WriteLine** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

### <a name="the-writeline-properties"></a>Proprietà di WriteLine
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.WriteLine> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.WriteLine>. Il valore predefinito è WriteLine. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Testo da scrivere. Per impostare la proprietà, digitare un'espressione Visual Basic nel **testo** casella il **WriteLine** attività della finestra di progettazione o nella griglia delle proprietà.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|Oggetto <xref:System.IO.TextWriter> nel quale <xref:System.Activities.Statements.WriteLine> scrive <xref:System.Activities.Statements.WriteLine.Text%2A>. Il valore predefinito corrisponde alla console.|

## <a name="see-also"></a>Vedere anche

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [ritardo](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)