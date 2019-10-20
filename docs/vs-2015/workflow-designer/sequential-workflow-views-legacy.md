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
ms.openlocfilehash: 8acc9bfcac476425ac6c6b967b1a3b3a34310d8a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663216"
---
# <a name="sequential-workflow-views-legacy"></a>Visualizzazioni del flusso di lavoro sequenziale (legacy)
In [!INCLUDE[vs2010](../includes/vs2010-md.md)] è presente un'utilità [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che è possibile usare per fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o a [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../includes/wf-md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le applicazioni [!INCLUDE[wf](../includes/wf-md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, comporre le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione.

 Quando si crea un flusso di lavoro sequenziale, ovvero un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), sono disponibili tre visualizzazioni del flusso di lavoro. Queste visualizzazioni sono accessibili dal menu **flusso di lavoro** e dal menu di scelta rapida nell'area di progettazione.

 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|Descrizione|
|----------------------|-----------------|
|**Visualizza SequentialWorkflow**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza SequentialWorkflow** dal menu di scelta rapida per visualizzare la visualizzazione del **flusso di lavoro sequenziale** , che mostra la rappresentazione grafica del flusso di lavoro sequenziale basata sull'attività. In alternativa, scegliere **Visualizza SequentialWorkflow** dal menu **flusso di lavoro** .|
|**Visualizza gestore Annulla**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore Annulla** dal menu di scelta rapida per visualizzare la visualizzazione del **flusso di lavoro sequenziale** , che mostra l'attività [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associata al flusso di lavoro. In alternativa, selezionare **Visualizza gestore Annulla** dal menu **flusso di lavoro** .|
|**Visualizza gestore errori**|Fare clic con il pulsante destro del mouse sull'area di progettazione e selezionare l'opzione **Visualizza gestore errori** dal menu di scelta rapida per visualizzare la visualizzazione **errori** , che mostra l'attività [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associata al flusso di lavoro. In alternativa, selezionare **Visualizza gestore errori** dal menu **flusso di lavoro** .|

 Per ulteriori informazioni su visualizzazioni simili, vedere [visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Visualizzazioni attività (legacy)](../workflow-designer/activity-views-legacy.md) [creazione](../workflow-designer/creating-legacy-workflow-projects.md) di flussi di lavoro legacy flussi di lavoro modalità di creazione [flussi](http://go.microsoft.com/fwlink?LinkID=65014) di lavoro