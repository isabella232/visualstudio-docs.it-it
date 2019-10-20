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
ms.openlocfilehash: c7d8a13890814b56865200acf95c8e0565b52b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655215"
---
# <a name="activity-views-legacy"></a>Visualizzazioni delle attività (legacy)
Per molte delle attività fornite da [!INCLUDE[wf](../includes/wf-md.md)], dalle quali vengono creati i flussi di lavoro, sono disponibili numerose visualizzazioni Progettazione in [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Quando si trascina un ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione e successivamente quando si seleziona l'attività, è possibile passare tra le diverse visualizzazioni di progettazione tramite il menu **flusso di lavoro** oppure facendo clic con il pulsante destro del mouse sull'oggetto selezionato attività. Quando si sposta il puntatore sul nome di un'attività selezionata, viene inoltre visualizzato un insieme a discesa di schede che è possibile usare per passare tra le diverse visualizzazioni.

 Ogni attività ha almeno una visualizzazione; si tratta della visualizzazione predefinita visualizzata quando si trascina un ActivityDesigner dalla **casella degli strumenti** nell'area di progettazione. Questa visualizzazione predefinita dell'attività è disponibile come opzione **Visualizza [tipo di attività]** nei menu e nella scheda, ad esempio, **Visualizza Parallel**. La maggior parte delle attività hanno visualizzazioni aggiuntive e attività diverse possono avere visualizzazioni diverse. Ad esempio, l'attività [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) ha la visualizzazione compensazione e l'attività [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) ha una visualizzazione eventi. Molte delle attività incluse in Windows Workflow Foundation hanno il **gestore di annullamento della visualizzazione** e le visualizzazioni di progettazione degli errori di **visualizzazione** per visualizzare i [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associati.

 Nella tabella riportata di seguito vengono elencati il nome e la descrizione di ogni visualizzazione.

|Opzione di menu/scheda|Descrizione|
|----------------------|-----------------|
|**Visualizzazione [tipo di attività]**|Selezionare questo menu o opzione della scheda per visualizzare la rappresentazione grafica predefinita dell'attività selezionata.|
|**Visualizza gestore Annulla**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associato all'attività selezionata.|
|**Visualizza gestore errori**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associato all'attività selezionata.|
|**Visualizza gestore compensazione**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associato al [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)selezionato.|
|**Visualizza gestore eventi**|Selezionare il menu o la visualizzazione delle opzioni di tabulazione per visualizzare il [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associato al [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)selezionato.|

 Per informazioni su visualizzazioni simili, vedere [visualizzazioni del flusso di lavoro sequenziale (legacy)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Vedere anche
 [Visualizzazioni flussi di lavoro sequenziali](../workflow-designer/sequential-workflow-views-legacy.md) delle [attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) (legacy)