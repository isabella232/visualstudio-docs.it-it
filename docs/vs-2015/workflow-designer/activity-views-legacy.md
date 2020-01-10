---
title: Visualizzazioni attività (legacy) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851473"
---
# <a name="activity-views-legacy"></a>Visualizzazioni delle attività (legacy)
Per molte delle attività fornite da [!INCLUDE[wf](../includes/wf-md.md)], dalle quali vengono creati i flussi di lavoro, sono disponibili numerose visualizzazioni Progettazione in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Quando si trascina un ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione e successivamente quando si seleziona l'attività, è possibile spostarsi tra le diverse visualizzazioni di progettazione utilizzando il menu **flusso di lavoro** o facendo clic con il pulsante destro del mouse sull'attività selezionata. Quando si sposta il puntatore sul nome di un'attività selezionata, viene inoltre visualizzato un insieme a discesa di schede che è possibile usare per passare tra le diverse visualizzazioni.

 Ogni attività ha almeno una visualizzazione; si tratta della visualizzazione predefinita visualizzata quando si trascina un ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione. Questa visualizzazione predefinita dell'attività è disponibile come opzione **Visualizza [tipo di attività]** nei menu e nella scheda, ad esempio, **Visualizza Parallel**. La maggior parte delle attività hanno visualizzazioni aggiuntive e attività diverse possono avere visualizzazioni diverse. Ad esempio, l'attività [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) ha la visualizzazione compensazione e l'attività [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) ha una visualizzazione eventi. Molte delle attività incluse in Windows Workflow Foundation hanno il **gestore di annullamento della visualizzazione** e le visualizzazioni di progettazione degli errori di **visualizzazione** per visualizzare i [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) e [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) associati.

 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|Descrizione|
|----------------------|-----------------|
|**Visualizzazione [tipo di attività]**|Selezionare questo menu o opzione della scheda per visualizzare la rappresentazione grafica predefinita dell'attività selezionata.|
|**Visualizza gestore Annulla**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) associato all'attività selezionata.|
|**Visualizza gestore errori**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) associato all'attività selezionata.|
|**Visualizza gestore compensazione**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) associato al [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)selezionato.|
|**Visualizza gestore eventi**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) associato al [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)selezionato.|

 Per informazioni su visualizzazioni simili, vedere [visualizzazioni del flusso di lavoro sequenziale (legacy)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Visualizzazioni flussi di lavoro sequenziali](../workflow-designer/sequential-workflow-views-legacy.md) delle [attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) (legacy)
