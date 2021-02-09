---
title: ActivityDesigner Progettazione flussi di lavoro-Interop
description: Informazioni sull'ActivityDesigner Interop e su come è possibile usare l'ActivityDesigner Interop per creare e configurare un'attività di interoperabilità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: edf4658743bb719c1c23f93b2d1d3cc33afdbaba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847388"
---
# <a name="interop-activity-designer"></a>ActivityDesigner Interop

L'ActivityDesigner **Interop** viene utilizzato per creare e configurare un' <xref:System.Activities.Statements.Interop> attività.

## <a name="the-interop-activity"></a>Attività Interop

L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.

### <a name="use-the-interop-activity-designer"></a>Usare l'ActivityDesigner Interop

L'ActivityDesigner **Interop** è disponibile nella categoria **migrazione** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** . In alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere **CTRL** + **ALT** + **X**.

La categoria di [migrazione](../workflow-designer/migration-activity-designers.md) che contiene l' <xref:System.Activities.Statements.Interop> attività viene visualizzata solo nella **casella degli strumenti** se il progetto è destinato .NET Framework 4 (completo) o versione successiva. Se necessario, è possibile modificare la versione del Framework di destinazione del progetto.

È possibile trascinare l'ActivityDesigner **Interop** dalla **casella degli strumenti** e rilasciarlo nell'area di progettazione flussi di lavoro quando vengono in genere posizionate le attività, ad esempio all'interno di un oggetto <xref:System.Activities.Statements.Sequence> . Se si elimina l'ActivityDesigner di **interoperabilità** , viene creata un' <xref:System.Activities.Statements.Interop> attività con un **DisplayName** predefinito di interoperabilità. È possibile modificare il <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Interop** oppure nella casella **DisplayName** della griglia delle proprietà.

Per aprire la finestra di dialogo **Cerca e seleziona un tipo .NET** , fare clic su **fare clic per sfogliare** il testo nella casella **ActivityType** nell'ActivityDesigner **Interop** o nella griglia delle proprietà. Vengono visualizzati solo i tipi per le attività flusso di lavoro 3,0 o flusso di lavoro 3,5. Ovvero vengono visualizzati solo i tipi derivati da <xref:System.Workflow.ComponentModel.Activity> . Per ulteriori informazioni sull'utilizzo di questa casella per specificare un tipo, vedere [finestra di dialogo Cerca e seleziona un tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Proprietà di Interop

Nella tabella seguente vengono illustrate le <xref:System.Activities.Statements.Interop> proprietà e viene descritto il modo in cui vengono utilizzate nella finestra di progettazione. Queste proprietà possono essere modificate nella griglia delle proprietà o nell'area di Progettazione flussi di lavoro.

|Nome proprietà|Obbligatoria|Utilizzo|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>. Il valore predefinito è **Interop**. Sebbene il nome visualizzato non sia obbligatorio, è consigliabile specificarne uno.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Vero|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>. Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vedi anche

- [Migrazione](../workflow-designer/migration-activity-designers.md)