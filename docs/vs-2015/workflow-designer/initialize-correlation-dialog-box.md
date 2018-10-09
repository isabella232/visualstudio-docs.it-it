---
title: Dialogo Inizializza correlazione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5dd09cea673411008a1c0d87dc26a781d212ab3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541085"
---
# <a name="initialize-correlation-dialog-box"></a>Finestra di dialogo Inizializza correlazione
Il **Inizializza correlazione** finestra di dialogo viene utilizzata nella [!INCLUDE[wfd1](../includes/wfd1-md.md)] per modificare la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà di un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività. [!INCLUDE[crdefault](../includes/crdefault-md.md)] il [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) argomento.  
  
 La tabella seguente descrive gli elementi dell'interfaccia utente di **Inizializza correlazione** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Correlazione**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> della correlazione da inizializzare.|  
|**Inizializzare su**|Coppia chiave/valore che contiene i dati da inizializzare. Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un esempio di coppia chiave/valore valida potrebbe essere una chiave denominata "OrderID" associata a una variabile denominata OrderID.|  
  
## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Per avviare la finestra di dialogo Inizializza correlazione  
  
-   Fare clic su **vista** nel **InitializeCorrelation** attività della finestra di progettazione o selezionare un <xref:System.ServiceModel.Activities.InitializeCorrelation> attività nella [!INCLUDE[wfd2](../includes/wfd2-md.md)] e quindi fare clic sui puntini di sospensione accanto al <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> proprietà in la griglia delle proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)