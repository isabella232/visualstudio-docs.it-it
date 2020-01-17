---
title: Finestra di dialogo Progettazione flussi di lavoro-Inizializza correlazione
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04f0a3bb70dbab31e0faa5c38caac9b54c6154fe
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114784"
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione

La finestra di dialogo **Inizializza correlazione** viene utilizzata in Progettazione flussi di lavoro per modificare la proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> di un'attività di <xref:System.ServiceModel.Activities.InitializeCorrelation>. Per ulteriori informazioni, vedere [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **Inizializza correlazione** :

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|
|**Inizializza su**|Coppia chiave/valore che contiene i dati da inizializzare. Questo valore corrisponde alla proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un esempio di coppia chiave/valore valida è una chiave denominata "OrderID" associata a una variabile denominata OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione

Fare clic su **Visualizza** nell'ActivityDesigner **InitializeCorrelation** o selezionare un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> in Progettazione flussi di lavoro. Fare quindi clic sul pulsante con i puntini di sospensione accanto alla proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> nella griglia delle proprietà.

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
