---
title: ActivityDesigner Interop | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659028"
---
# <a name="interop-activity-designer"></a>ActivityDesigner Interop
L'ActivityDesigner **Interop** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Attività Interop
 L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.

### <a name="using-the-interop-activity-designer"></a>Utilizzo dell'ActivityDesigner Interop
 L'ActivityDesigner **Interop** è disponibile nella categoria **migrazione** della **casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **casella degli strumenti** . in alternativa, scegliere **casella degli strumenti** dal menu **Visualizza** o premere CTRL + ALT + X.

 La categoria di [migrazione](../workflow-designer/migration-activity-designers.md) che contiene l'attività <xref:System.Activities.Statements.Interop> viene visualizzata nella **casella degli strumenti** solo se il progetto è destinato alla [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] completa.

 Per C# i progetti, è possibile ridefinire la destinazione del progetto in modo da utilizzare il [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] completo facendo clic con il pulsante destro del mouse sul progetto nel **Esplora soluzioni** e selezionando **proprietà**. Nella scheda **applicazione** selezionare l'opzione **.NET Framework 4** nel **Framework di destinazione**. Selezionare il pulsante **Sì** nella finestra di dialogo di **modifica del Framework di destinazione** in cui viene chiesto di confermare la modifica.

 Per i progetti VB, è possibile ridefinire la destinazione del progetto in modo da usare il [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] completo facendo clic con il pulsante destro del mouse sul progetto nel **Esplora soluzioni** e selezionando **Proprietà**. Nella scheda **compilazione** fare clic sul pulsante **Opzioni di compilazione avanzate** . Selezionare **.NET Framework 4** dall' **elenco Framework di destinazione** e quindi fare clic su **OK**. Fare clic sul pulsante **Sì** nella finestra di dialogo di **modifica del Framework di destinazione** in cui viene chiesto di confermare la modifica.

 È possibile trascinare l'ActivityDesigner di **interoperabilità** dalla **casella degli strumenti** e rilasciarlo nell'area [!INCLUDE[wfd2](../includes/wfd2-md.md)] quando vengono in genere posizionate le attività, ad esempio all'interno di un <xref:System.Activities.Statements.Sequence>. In questo modo viene creata un'attività di <xref:System.Activities.Statements.Interop> con un **DisplayName** predefinito di interoperabilità. Il <xref:System.Activities.Activity.DisplayName%2A> può essere modificato nell'intestazione dell'ActivityDesigner **Interop** o nella casella **DisplayName** della griglia delle proprietà.

 Fare clic su **fare clic per sfogliare...** per visualizzare la finestra di dialogo **Cerca e seleziona un tipo .NET** , nella casella **ActivityType** dell'ActivityDesigner **Interop** o della griglia delle proprietà. Vengono visualizzati solo i tipi relativi alle attività del flusso di lavoro 3.0 o del flusso di lavoro 3.5, ovvero solo i tipi derivati da <xref:System.Workflow.ComponentModel.Activity>. [!INCLUDE[crabout](../includes/crabout-md.md)] usare questa casella per specificare un tipo, vedere l'argomento [individuare e selezionare un tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Proprietà di Interop
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Interop> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome proprietà|Richiesto|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>. L'impostazione predefinita è Interop. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>. Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vedere anche
 [Migrazione](../workflow-designer/migration-activity-designers.md)