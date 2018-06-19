---
title: Finestra di progettazione del flusso di lavoro - ActivityDesigner Interop
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb9eb5e8b2dbca57d28f9d350b769b5eaa90e2b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979074"
---
# <a name="interop-activity-designer"></a>ActivityDesigner Interop

Il **interoperabilità** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Interop> attività.

## <a name="the-interop-activity"></a>Attività Interop
 L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.

### <a name="using-the-interop-activity-designer"></a>Utilizzo dell'ActivityDesigner Interop
 Il **interoperabilità** ActivityDesigner è reperibile nel **migrazione** categoria del **della casella degli strumenti**, accessibile facendo clic il **dellacaselladeglistrumenti**scheda (in alternativa, selezionare **della casella degli strumenti** dal **vista** menu o CTRL + ALT + X.)

 Il [migrazione](../workflow-designer/migration-activity-designers.md) categoria che contiene il <xref:System.Activities.Statements.Interop> attività si manifesta solo nella **casella degli strumenti** se il progetto è destinato a .NET Framework 4 full.

 Per i progetti c#, è possibile modificare la destinazione del progetto per utilizzare la versione completa di .NET Framework 4 facendo clic con il progetto nel **Esplora soluzioni** e selezionando **proprietà**. Nel **applicazione** , selezionare il **NET Framework 4** opzione il **framework di destinazione**. Selezionare il **Sì** pulsante il **modifica Framework di destinazione** finestra di dialogo che verrà richiesto di confermare la modifica.

 Per i progetti di Visual Basic, è possibile modificare la destinazione del progetto per utilizzare la versione completa di .NET Framework 4 facendo clic sul progetto nel **Esplora soluzioni** e selezionando **proprietà**. Nel **compilare** scheda, fare clic su di **opzioni di compilazione avanzate** pulsante. Selezionare **.Net Framework 4** dal **elenco framework di destinazione** e quindi fare clic su **OK**. Fare clic su di **Sì** pulsante il **modifica Framework di destinazione** finestra di dialogo che verrà richiesto di confermare la modifica.

 Il **interoperabilità** ActivityDesigner può essere trascinato dal **casella degli strumenti** e rilasciate sull'area di progettazione flussi di lavoro ogni volta che le attività vengono in genere posizionate, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Crea un <xref:System.Activities.Statements.Interop> attività con valore predefinito è **DisplayName** di interoperabilità. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **interoperabilità** ActivityDesigner o nel **DisplayName** casella della griglia delle proprietà.

 Fare clic su di **fare clic per Sfoglia...**  testo il **ActivityType** casella, nel **interoperabilità** attività della finestra di progettazione o nella griglia delle proprietà, per visualizzare il **Cerca e seleziona .net tipo** la finestra di dialogo. Vengono visualizzati solo i tipi relativi alle attività del flusso di lavoro 3.0 o del flusso di lavoro 3.5, ovvero solo i tipi derivati da <xref:System.Workflow.ComponentModel.Activity>. Per ulteriori informazioni sull'utilizzo di questa casella per specificare un tipo, vedere il [individuare e selezionare una finestra di dialogo di tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) argomento.

### <a name="the-interop-properties"></a>Proprietà di Interop
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Interop> e ne viene descritta la modalità di utilizzo nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia proprietà o nell'area di progettazione flussi di lavoro.

|Nome proprietà|Obbligatorio|Utilizzo|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>. L'impostazione predefinita è Interop. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>. Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Vedere anche

- [Migrazione](../workflow-designer/migration-activity-designers.md)