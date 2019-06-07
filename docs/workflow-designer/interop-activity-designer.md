---
title: Finestra di progettazione del flusso di lavoro, ActivityDesigner Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688ef92fae5bd0cbaa5ddc653bbaab5692f4827f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747144"
---
# <a name="interop-activity-designer"></a>ActivityDesigner Interop

Il **Interop** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Interop> attività.

## <a name="the-interop-activity"></a>Attività Interop

L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.

### <a name="use-the-interop-activity-designer"></a>Utilizzo dell'ActivityDesigner Interop

Il **interoperabilità** ActivityDesigner è reperibile nel **migrazione** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**scheda. In alternativa, selezionare **della casella degli strumenti** dal **View** dal menu oppure premere **Ctrl**+**Alt** + **X**.

Il [Migration](../workflow-designer/migration-activity-designers.md) categoria che contiene il <xref:System.Activities.Statements.Interop> attività viene visualizzata solo **della casella degli strumenti** se il progetto è destinato a .NET Framework 4 (completo) o versione successiva. Se necessario, è possibile modificare la versione di framework che le destinazioni del progetto.

Il **Interop** ActivityDesigner può essere trascinato dalla **della casella degli strumenti** e rilasciate nell'area di progettazione del flusso di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Eliminando il **Interop** crea ActivityDesigner un' <xref:System.Activities.Statements.Interop> attività con un valore predefinito **DisplayName** di interoperabilità. È possibile modificare il <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione del **interoperabilità** ActivityDesigner, o nel **DisplayName** finestra della griglia delle proprietà.

Fare clic sul **fare clic per passare** testo nel **ActivityType** finestra, nel **interoperabilità** della finestra di progettazione oppure nella griglia delle proprietà per aprire il **Sfoglia e Selezionare .net tipo** nella finestra di dialogo. Vengono visualizzati solo i tipi di flusso di lavoro 3.0 o le attività del flusso di lavoro 3.5. Vale a dire, solo i tipi derivati da <xref:System.Workflow.ComponentModel.Activity> vengono visualizzati. Per altre informazioni sull'uso di questa casella per specificare un tipo, vedere [individuare e selezionare una finestra di dialogo tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Proprietà di Interop

La tabella seguente illustra il <xref:System.Activities.Statements.Interop> proprietà e viene descritto come usarle nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area di progettazione del flusso di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>. Il valore predefinito è **interoperabilità**. Anche se il nome visualizzato non è obbligatorio, è consigliabile per fornirne una.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>. Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vedere anche

- [Migrazione](../workflow-designer/migration-activity-designers.md)