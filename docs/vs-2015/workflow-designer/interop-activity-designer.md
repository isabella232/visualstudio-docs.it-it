---
title: Activity Designer Interop | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965031"
---
# <a name="interop-activity-designer"></a>ActivityDesigner Interop
Il **Interop** ActivityDesigner viene utilizzato per creare e configurare un <xref:System.Activities.Statements.Interop> attività.  
  
## <a name="the-interop-activity"></a>Attività Interop  
 L'attività <xref:System.Activities.Statements.Interop> gestisce l'esecuzione dei tipi che derivano da <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> all'interno di un flusso di lavoro.  
  
### <a name="using-the-interop-activity-designer"></a>Utilizzo dell'ActivityDesigner Interop  
 Il **interoperabilità** ActivityDesigner è reperibile nel **migrazione** categoria del **della casella degli strumenti**, accessibile facendo clic di **della casella degli strumenti**scheda (in alternativa, selezionare **casella degli strumenti** dal **visualizzazione** menu o CTRL + ALT + X.)  
  
 Il [Migration](../workflow-designer/migration-activity-designers.md) categoria che contiene il <xref:System.Activities.Statements.Interop> attività si manifesta solo nella **della casella degli strumenti** se il progetto è destinato alla versione completa [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 Per i progetti C#, è possibile modificare la destinazione del progetto per usare la versione completa [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] facendo clic con il progetto nel **Esplora soluzioni** e selezionando **proprietà**. Nel **Application** scheda, seleziona il **NET Framework 4** opzione il **framework di destinazione**. Selezionare il **Yes** pulsante nel **Modifica versione .NET Framework di destinazione** finestra di dialogo che verrà richiesto di confermare la modifica.  
  
 Per i progetti Visual Basic, è possibile modificare la destinazione del progetto per usare la versione completa [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] destro del mouse sul progetto nel **Esplora soluzioni** e selezionando **proprietà**. Nel **Compile** scheda, fare clic sui **opzioni di compilazione avanzate** pulsante. Selezionare **.Net Framework 4** dalle **elenco framework di destinazione** e quindi fare clic su **OK**. Fare clic sul **Yes** pulsante nel **Modifica versione .NET Framework di destinazione** finestra di dialogo che verrà richiesto di confermare la modifica.  
  
 Il **Interop** ActivityDesigner può essere trascinato dal **della casella degli strumenti** e rilasciato nel [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie ovunque posizionate le attività vengono in genere, ad esempio all'interno un <xref:System.Activities.Statements.Sequence>. Ciò consente di creare un <xref:System.Activities.Statements.Interop> attività con un valore predefinito **DisplayName** di interoperabilità. Il <xref:System.Activities.Activity.DisplayName%2A> possono essere modificati nell'intestazione del **interoperabilità** ActivityDesigner o nel **DisplayName** finestra della griglia delle proprietà.  
  
 Fare clic su di **fare clic per cercare...** testo nel **ActivityType** casella nel **interoperabilità** attività della finestra di progettazione o nella griglia delle proprietà, per visualizzare il **Cerca e seleziona un .net tipo** nella finestra di dialogo. Vengono visualizzati solo i tipi relativi alle attività del flusso di lavoro 3.0 o del flusso di lavoro 3.5, ovvero solo i tipi derivati da <xref:System.Workflow.ComponentModel.Activity>. [!INCLUDE[crabout](../includes/crabout-md.md)] utilizzo di questa casella per specificare un tipo, vedere la [individuare e selezionare una finestra di dialogo tipo .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) argomento.  
  
### <a name="the-interop-properties"></a>Proprietà di Interop  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Interop> e ne viene descritta la modalità di uso nella finestra di progettazione. Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area di [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Interop>. L'impostazione predefinita è Interop. Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'uso.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Consente di specificare il tipo di attività incluso nell'attività <xref:System.Activities.Statements.Interop>. Tale tipo specificato deve derivare da <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione](../workflow-designer/migration-activity-designers.md)