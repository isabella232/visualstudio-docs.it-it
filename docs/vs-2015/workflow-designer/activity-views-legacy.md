---
title: Visualizzazioni delle attività (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62b3c9185226512ff28c8d028cd0ba7d33b0f12f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977446"
---
# <a name="activity-views-legacy"></a>Visualizzazioni delle attività (legacy)
Per molte delle attività fornite da [!INCLUDE[wf](../includes/wf-md.md)], dalle quali vengono creati i flussi di lavoro, sono disponibili numerose visualizzazioni Progettazione in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Quando si trascina un ActivityDesigner dal **casella degli strumenti** nell'area di progettazione e successivamente ogni volta che si seleziona l'attività, è possibile passare tra le diverse visualizzazioni Progettazione usando il **flusso di lavoro**menu o facendo clic con l'attività selezionata. Quando si sposta il puntatore sul nome di un'attività selezionata, viene inoltre visualizzato un insieme a discesa di schede che è possibile usare per passare tra le diverse visualizzazioni.  
  
 Ogni attività dispone di almeno una visualizzazione. Questa è la visualizzazione predefinita quando si trascina un ActivityDesigner dal **casella degli strumenti** nell'area di progettazione. Questa visualizzazione predefinita dell'attività è disponibile come le **Visualizza [tipo di attività]** opzione nel menu e nella scheda, ad esempio **visualizzazione Parallel**. La maggior parte delle attività hanno visualizzazioni aggiuntive e attività diverse possono avere visualizzazioni diverse. Ad esempio, il [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) attività presenta la visualizzazione di compensazione e il [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) attività dispone di un eventi vista. Molte delle attività fornite con Windows Workflow Foundation dispongono **Visualizza gestore annullamento** e **visualizzazione errori** visualizzazioni alla visualizzazione di progettazione di [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) essi associati.  
  
 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.  
  
|Opzione di menu/scheda|Descrizione|  
|----------------------|-----------------|  
|**Visualizzazione [tipo di attività]**|Selezionare questo menu o opzione della scheda per visualizzare la rappresentazione grafica predefinita dell'attività selezionata.|  
|**Visualizza gestore annullamento**|Selezionare questo menu o opzione della scheda per visualizzare il [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associato all'attività selezionata.|  
|**Visualizza gestori errori**|Selezionare questo menu o opzione della scheda per visualizzare il [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associato all'attività selezionata.|  
|**Visualizza gestore di compensazione**|Selezionare questo menu o opzione della scheda per visualizzare il [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associate all'elemento selezionato [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Visualizzazione eventi gestore**|Selezionare questo menu o opzione della scheda per visualizzare il [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associate all'elemento selezionato le [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Per informazioni su visualizzazioni simili, vedere [visualizzazioni del flusso di lavoro sequenziale (Legacy)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Visualizzazioni del flusso di lavoro sequenziale (legacy)](../workflow-designer/sequential-workflow-views-legacy.md)