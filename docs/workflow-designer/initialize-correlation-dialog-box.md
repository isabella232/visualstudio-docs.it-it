---
title: Progettazione flussi di lavoro finestra di dialogo Inizializza correlazione
description: Informazioni su come usare la finestra di dialogo Inizializza correlazione nel Progettazione flussi di lavoro per modificare la proprietà CorrelationData di un'attività InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 123fa7a3b9a9cbc65ed458ab5b412268f00dd15001148db26915c4ddf882845a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121267052"
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione

La **finestra di dialogo** Inizializza correlazione viene usata Progettazione flussi di lavoro per modificare la proprietà di <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> <xref:System.ServiceModel.Activities.InitializeCorrelation> un'attività. Per altre informazioni, vedere [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

La tabella seguente descrive gli elementi dell'interfaccia utente della finestra di dialogo **Inizializza** correlazione:

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|
|**Inizializza in**|Coppia chiave/valore che contiene i dati da inizializzare. Questo valore corrisponde alla <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà . Un esempio di coppia chiave/valore valida è una chiave denominata "OrderID" associata a una variabile denominata OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione

Fare **clic su** Visualizza **nell'ActivityDesigner InitializeCorrelation** o selezionare <xref:System.ServiceModel.Activities.InitializeCorrelation> un'attività in Progettazione flussi di lavoro. Fare quindi clic sul pulsante con i puntini di sospensione accanto alla <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà nella griglia delle proprietà.

## <a name="see-also"></a>Vedi anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
