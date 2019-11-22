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
ms.openlocfilehash: 859fa44b44a295dc3e9f27fc168092a9fe2beebf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292361"
---
# <a name="sequential-workflow-views-legacy"></a>Visualizzazioni del flusso di lavoro sequenziale (legacy)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] fornisce una [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che può essere usata per la destinazione del [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o del [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../includes/wf-md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le applicazioni [!INCLUDE[wf](../includes/wf-md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **Casella degli strumenti** nell'area di progettazione.

 Quando si crea un flusso di lavoro sequenziale, ovvero un [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040), sono disponibili tre visualizzazioni del flusso di lavoro. Queste visualizzazioni sono accessibili dal menu **Flusso di lavoro** e dal menu di scelta rapida nell'area di progettazione.

 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|description|
|----------------------|-----------------|
|**Visualizza SequentialWorkflow**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza Flusso di lavoro sequenziale** nel menu di scelta rapida per aprire la visualizzazione **Flusso di lavoro sequenziale** in cui viene mostrata la rappresentazione grafica basata sull'attività del flusso di lavoro sequenziale. In alternativa, selezionare **Visualizza Flusso di lavoro sequenziale** nel menu **Flusso di lavoro**.|
|**Visualizza gestore Annulla**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore Annulla** dal menu di scelta rapida per visualizzare la visualizzazione del **flusso di lavoro sequenziale** , che mostra l'attività [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) associata al flusso di lavoro. In alternativa, selezionare **Visualizza gestore annullamento** nel menu **Flusso di lavoro**.|
|**Visualizza gestore errori**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore errori** dal menu di scelta rapida per visualizzare la visualizzazione **errori** , che mostra l'attività [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) associata al flusso di lavoro. In alternativa, selezionare **Visualizza gestori errori** dal menu **Flusso di lavoro**.|

 Per ulteriori informazioni su visualizzazioni simili, vedere [visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md) [creazione](../workflow-designer/creating-legacy-workflow-projects.md) di flussi di lavoro legacy flussi di lavoro modalità di creazione [flussi](https://go.microsoft.com/fwlink?LinkID=65014) di lavoro