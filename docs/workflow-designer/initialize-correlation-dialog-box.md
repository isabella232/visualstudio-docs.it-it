---
title: Finestra di progettazione del flusso di lavoro - finestra di dialogo Inizializza correlazione
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: edfdef1c1f946e2c5f677d0ff1578a40ea7bcd8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906234"
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