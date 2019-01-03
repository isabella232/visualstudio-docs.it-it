---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Inizializza correlazione
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f001e053b0c2fdfe892175b00ed3f39dc6f1b4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829761"
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione

Il **Inizializza correlazione** finestra di dialogo viene utilizzata nella finestra di progettazione del flusso di lavoro per modificare le <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà di un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività. Per altre informazioni, vedere [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

La tabella seguente descrive gli elementi dell'interfaccia utente di **Inizializza correlazione** nella finestra di dialogo:

|Elemento dell'interfaccia utente|Descrizione|
|-|-----------------|
|**Correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|
|**Inizializzare su**|Coppia chiave/valore che contiene i dati da inizializzare. Questo valore corrisponde al <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà. Un esempio di una coppia chiave/valore valido è una chiave denominata "OrderID" associata a una variabile denominata OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione

Fare clic su **View** nel **InitializeCorrelation** attività della finestra di progettazione o selezionare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività nella finestra di progettazione del flusso di lavoro. Quindi, fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà nella griglia delle proprietà.

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)