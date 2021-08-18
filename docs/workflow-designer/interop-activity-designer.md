---
title: Progettazione flussi di lavoro - ActivityDesigner Interop
description: Informazioni sull'ActivityDesigner Interop e su come usare l'ActivityDesigner Interop per creare e configurare un'attività Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 785fa491d78c0286404918f01149752af2f0dc69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045853"
---
# <a name="interop-activity-designer"></a>ActivityDesigner Interop

**L'ActivityDesigner** Interop viene usato per creare e configurare un'attività. <xref:System.Activities.Statements.Interop>

## <a name="the-interop-activity"></a>Attività Interop

L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.

### <a name="use-the-interop-activity-designer"></a>Usare l'ActivityDesigner Interop

L'ActivityDesigner Interoperabilità è disponibile nella **categoria Migrazione** della Casella degli strumenti **,** a cui si accede facendo clic sulla scheda **Casella degli** strumenti .  In alternativa, scegliere **Casella degli** strumenti **dal** menu Visualizza o premere **CTRL** + **ALT** + **X.**

La [categoria Migrazione](../workflow-designer/migration-activity-designers.md) che contiene l'attività viene visualizzata nella casella degli strumenti solo se il progetto è destinato .NET Framework <xref:System.Activities.Statements.Interop> 4 (completo) o versione successiva.  Se necessario, è possibile modificare la versione del framework di destinazione del progetto.

**L'ActivityDesigner** Interop può  essere trascinato dalla casella degli strumenti e rilasciato nella Progettazione flussi di lavoro in cui in genere vengono inserite attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . L'eliminazione **dell'ActivityDesigner** Interop crea <xref:System.Activities.Statements.Interop> un'attività con **un valore DisplayName predefinito** di Interop. È possibile modificare <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Interop** o nella **casella DisplayName** della griglia delle proprietà.

Fare clic **su** Fare clic per visualizzare il testo nella casella **ActivityType** , nell'ActivityDesigner **Interop**  o nella griglia delle proprietà, per aprire la finestra di dialogo Sfoglia e seleziona un **tipo .NET** . Vengono visualizzati solo i tipi per le attività del flusso di lavoro 3.0 o del flusso di lavoro 3.5. Ciò significa che vengono visualizzati solo i <xref:System.Workflow.ComponentModel.Activity> tipi derivati da . Per altre informazioni sull'uso di questa casella per specificare un tipo, vedere Finestra di dialogo Sfoglia e seleziona un tipo [.NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Proprietà di Interop

Nella tabella seguente vengono illustrate <xref:System.Activities.Statements.Interop> le proprietà e viene descritto come vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o nella Progettazione flussi di lavoro proprietà.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>. Il valore predefinito è **Interop.** Anche se il nome visualizzato non è obbligatorio, è consigliabile specificarne uno.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Vero|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>. Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vedi anche

- [Migrazione](../workflow-designer/migration-activity-designers.md)