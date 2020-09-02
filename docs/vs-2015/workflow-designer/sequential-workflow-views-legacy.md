---
title: Visualizzazioni del flusso di lavoro sequenziale (legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846208"
---
# <a name="sequential-workflow-views-legacy"></a>Visualizzazioni del flusso di lavoro sequenziale (legacy)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] fornisce un legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)] che può essere utilizzato per fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../includes/wf-md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le applicazioni [!INCLUDE[wf](../includes/wf-md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, comporre le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione.

 Quando si crea un flusso di lavoro sequenziale, ovvero un [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx), sono disponibili tre visualizzazioni del flusso di lavoro. Queste visualizzazioni sono accessibili dal menu **flusso di lavoro** e dal menu di scelta rapida nell'area di progettazione.

 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|Descrizione|
|----------------------|-----------------|
|**Visualizza Flusso di lavoro sequenziale**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza SequentialWorkflow** dal menu di scelta rapida per visualizzare la visualizzazione del **flusso di lavoro sequenziale** , che mostra la rappresentazione grafica del flusso di lavoro sequenziale basata sull'attività. In alternativa, scegliere **Visualizza SequentialWorkflow** dal menu **flusso di lavoro** .|
|**Visualizza gestore annullamento**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore Annulla** dal menu di scelta rapida per visualizzare la visualizzazione del **flusso di lavoro sequenziale** , che mostra l'attività [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) associata al flusso di lavoro. In alternativa, selezionare **Visualizza gestore Annulla** dal menu **flusso di lavoro** .|
|**Visualizza gestore errori**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore errori** dal menu di scelta rapida per visualizzare la visualizzazione **errori** , che mostra l'attività [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) associata al flusso di lavoro. In alternativa, selezionare **Visualizza gestore errori** dal menu **flusso di lavoro** .|

 Per ulteriori informazioni su visualizzazioni simili, vedere [visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md) [creazione](../workflow-designer/creating-legacy-workflow-projects.md) di flussi di lavoro legacy flussi di lavoro modalità di creazione [flussi](https://msdn2.microsoft.com/library/bb628440.aspx) di lavoro
