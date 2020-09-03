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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114784"
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione

La finestra di dialogo **Inizializza correlazione** viene utilizzata in Progettazione flussi di lavoro per modificare la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà di un' <xref:System.ServiceModel.Activities.InitializeCorrelation> attività. Per ulteriori informazioni, vedere [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente (UI) della finestra di dialogo **Inizializza correlazione** :

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|
|**Inizializza in**|Coppia chiave/valore che contiene i dati da inizializzare. Questo valore corrisponde alla <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Proprietà. Un esempio di coppia chiave/valore valida è una chiave denominata "OrderID" associata a una variabile denominata OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione

Fare clic su **Visualizza** nell'ActivityDesigner **InitializeCorrelation** o selezionare un' <xref:System.ServiceModel.Activities.InitializeCorrelation> attività in Progettazione flussi di lavoro. Fare quindi clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà nella griglia delle proprietà.

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
