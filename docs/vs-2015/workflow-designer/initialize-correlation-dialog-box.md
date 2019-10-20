---
title: Finestra di dialogo Inizializza correlazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659047"
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione
La finestra di dialogo **Inizializza correlazione** viene utilizzata in [!INCLUDE[wfd1](../includes/wfd1-md.md)] per modificare la proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> di un'attività di <xref:System.ServiceModel.Activities.InitializeCorrelation>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] argomento [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Inizializza correlazione** .

|Elemento dell'interfaccia utente|Descrizione|
|----------------|-----------------|
|**Correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|
|**Inizializza su**|Coppia chiave/valore che contiene i dati da inizializzare. Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un esempio di coppia chiave/valore valida potrebbe essere una chiave denominata "OrderID" associata a una variabile denominata OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione

- Fare clic su **Visualizza** nell'ActivityDesigner **InitializeCorrelation** o selezionare un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> in [!INCLUDE[wfd2](../includes/wfd2-md.md)] e quindi fare clic sul pulsante con i puntini di sospensione accanto alla proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> nella griglia delle proprietà.

## <a name="see-also"></a>Vedere anche
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)