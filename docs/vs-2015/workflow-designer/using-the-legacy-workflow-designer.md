---
title: Uso del Progettazione flussi di lavoro legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72c92b4431c21c27bc1fe2ff86b24c850cc34694
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846086"
---
# <a name="using-the-legacy-workflow-designer"></a>Utilizzo di Progettazione flussi di lavoro legacy
La [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)] può essere usata per fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o a [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 È possibile accedervi selezionando l'opzione **.NET Framework 3,0** o l'opzione **.NET Framework 3,5** nell'elenco a discesa nella parte superiore della finestra **nuovo progetto** . L'opzione predefinita in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è **.NET Framework 4** utilizzata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] destinate al [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../includes/wf-md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le applicazioni [!INCLUDE[wf](../includes/wf-md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, comporre le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione.

 Nella tabella seguente sono elencate le funzionalità principali di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per Windows Workflow Foundation.

|Caratteristica|Descrizione|
|-------------|-----------------|
|Attività di trascinamento della selezione|Trascinare le attività dalla **casella degli strumenti** nell'area di progettazione per creare un flusso di lavoro.|
|Visualizzatore proprietà|La finestra **Proprietà** standard in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene utilizzata per configurare le proprietà di un'attività.|
|Zoom|L'icona del **livello di zoom** del binocolo si trova sotto la barra di scorrimento verticale sul lato destro dell'area di progettazione. Fare clic sui binocoli e selezionare una percentuale di zoom per ingrandire o ridurre il grafico del flusso di lavoro. Per eseguire lo zoom avanti e indietro, è anche possibile usare le opzioni del cursore della lente di ingrandimento dell'icona **Panoramica** .|
|Panoramica|L'icona a forma di **Pan** , un cerchio che contiene quattro frecce incrociate che puntano in quattro direzioni, si trova sotto la barra di scorrimento verticale sul lato destro dell'area di progettazione immediatamente sotto l'icona dello zoom del binocolo. Facendo clic sull'icona di panoramica, le opzioni del cursore seguenti verranno offerte da un menu a comparsa:<br /><br /> -Il cursore **zoom avanti** lente di ingrandimento consente di eseguire lo zoom avanti facendo clic sull'area di progettazione.<br />-Il cursore **Zoom indietro** lente di ingrandimento consente di eseguire lo zoom indietro facendo clic sull'area di progettazione.<br />-Il cursore a forma di mano dello **strumento di navigazione** consente di "selezionare" e spostare la visualizzazione di un flusso di lavoro nell'area di progettazione.<br />-Il cursore freccia **predefinito** consente di tornare dagli altri cursori al cursore freccia predefinito.|
|Scorrimento automatico|Se si ha un grande flusso di lavoro, è necessario posizionare un'attività oltre la visualizzazione visibile dell'area di progettazione. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] consente di trascinare un'attività verso il bordo dell'area di progettazione nel punto più vicino a dove si desidera inserire l'attività. La visualizzazione dell'area di progettazione scorre automaticamente in quella direzione.|
|Smart tag|Le attività la cui configurazione non è completa o valida sono contrassegnate da un'icona di punto esclamativo. È possibile fare clic sull'icona e visualizzare un elenco a discesa di richieste di configurazione esistenti sull'attività. È quindi possibile usare la finestra **Proprietà** per configurare l'attività in modo appropriato. Quando tutte le proprietà sono valide per l'attività, l'icona di punto esclamativo scompare.|

## <a name="in-this-section"></a>In questa sezione
 [Finestre del flusso di lavoro di Visual Studio (legacy)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md)

 [Visualizzazioni del flusso di lavoro sequenziale (legacy)](../workflow-designer/sequential-workflow-views-legacy.md)

 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)

 [Uso di temi in flussi di lavoro (legacy)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [Uso della finestra di progettazione flusso di lavoro di una macchina a stati (legacy)](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [Uso dell'Activity Designer legacy](../workflow-designer/using-the-legacy-activity-designer.md)

 [Finestra di progettazione legacy per la Guida interfaccia utente di Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>Vedere anche
 [Sviluppo di flussi di lavoro](https://msdn2.microsoft.com/library/bb628448.aspx)
