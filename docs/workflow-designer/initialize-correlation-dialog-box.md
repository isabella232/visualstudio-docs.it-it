---
title: Inizializzare la finestra di dialogo di correlazione | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 641526a0577c74ff590d701560e5266c85fa60dc
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione

Il **Inizializza correlazione** in Progettazione flussi di lavoro di Windows utilizzata per modificare la finestra di dialogo di <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà di un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività. Per ulteriori informazioni, vedere il [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) argomento.

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente di **Inizializza correlazione** la finestra di dialogo.

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|
|**Inizializzare in**|Coppia chiave/valore che contiene i dati da inizializzare. Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un esempio di una coppia chiave/valore valida potrebbe essere una chiave denominata "OrderID" associata a una variabile denominata OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione

-   Fare clic su **vista** sul **InitializeCorrelation** attività della finestra di progettazione oppure selezionare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] e quindi fare clic sul pulsante con i puntini di sospensione accanto al <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà in la griglia delle proprietà.

## <a name="see-also"></a>Vedere anche

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)