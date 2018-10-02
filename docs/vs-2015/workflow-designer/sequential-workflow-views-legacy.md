---
title: Visualizzazioni del flusso di lavoro sequenziale (Legacy) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 46c37ec7f3813078b9e70076bf92e6d0e1b86453
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532222"
---
# <a name="sequential-workflow-views-legacy"></a>Visualizzazioni del flusso di lavoro sequenziale (legacy)
In [!INCLUDE[vs2010](../includes/vs2010-md.md)] è presente un'utilità [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy che è possibile usare per fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o a [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [!INCLUDE[wfd2](../includes/wfd2-md.md)] consente di creare graficamente le applicazioni di [!INCLUDE[wf](../includes/wf-md.md)] usando dell'interfaccia utente comune di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le applicazioni [!INCLUDE[wf](../includes/wf-md.md)]sono composte da passaggi del processo del flusso di lavoro chiamati attività. Per creare un flusso di lavoro, creare le attività nell'area di progettazione trascinando i rispettivi ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione.  
  
 Quando si crea un flusso di lavoro sequenza, che è un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), sono disponibili tre visualizzazioni del flusso di lavoro. Queste visualizzazioni sono accessibili dal **flusso di lavoro** menu e dal menu di scelta rapida nell'area di progettazione.  
  
 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.  
  
|Opzione di menu/scheda|Descrizione|  
|----------------------|-----------------|  
|**Vista flusso di lavoro sequenziale**|Fare doppio clic su area di progettazione e seleziona il **Visualizza flusso di lavoro sequenziale** opzione dal menu di scelta rapida per visualizzare i **flusso di lavoro sequenziale** visualizzazione, che mostra le attività basate su grafici rappresentazione del flusso di lavoro sequenza. Oppure selezionare **Visualizza flusso di lavoro sequenziale** dalle **flusso di lavoro** menu.|  
|**Visualizza gestore annullamento**|Fare doppio clic su area di progettazione e seleziona il **Visualizza gestore annullamento** opzione dal menu di scelta rapida per visualizzare i **flusso di lavoro sequenziale** che mostra il [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) attività associata con il flusso di lavoro. Oppure selezionare **Visualizza gestore annullamento** dalle **flusso di lavoro** menu.|  
|**Visualizza gestori errori**|Fare doppio clic su area di progettazione e seleziona il **Visualizza gestori errori** opzione dal menu di scelta rapida per visualizzare i **errori** che mostra il [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) attività associata con il flusso di lavoro. Oppure selezionare **Visualizza gestori errori** dalle **flusso di lavoro** menu.|  
  
 Per altre informazioni su visualizzazioni simili, vedere [visualizzazioni delle attività (Legacy)](../workflow-designer/activity-views-legacy.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazioni delle attività (Legacy)](../workflow-designer/activity-views-legacy.md)   
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modalità di creazione del flusso di lavoro](http://go.microsoft.com/fwlink?LinkID=65014)