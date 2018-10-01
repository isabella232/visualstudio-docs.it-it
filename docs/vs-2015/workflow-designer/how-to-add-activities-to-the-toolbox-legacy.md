---
title: 'Procedura: aggiungere attività alla casella degli strumenti (Legacy) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0bcd5f525dfb0794f06b5210287251feb883b340
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527697"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procedura: aggiungere attività nella Casella degli strumenti [legacy]
Quando si compila una soluzione del flusso di lavoro con legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)] che fa riferimento al [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o il [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], le attività personalizzate possono essere aggiunti al progetto del flusso di lavoro e agli ActivityDesigner disponibili nella **della casella degli strumenti** per semplice accesso. È anche possibile aggiungere le attività direttamente la **casella degli strumenti** da una libreria di collegamento dinamico (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Per aggiungere un'attività nella Casella degli strumenti da una DLL  
  
1.  Il pulsante destro della casella degli strumenti finestra sotto **flusso di lavoro di Windows**, quindi fare clic su **Scegli elementi**.  
  
2.  Nel **Scegli elementi della casella degli strumenti** della finestra di dialogo fare clic sui **componenti System. Activities** scheda e quindi fare clic su **Sfoglia** dal lato inferiore destro della finestra.  
  
3.  Selezionare la DLL dalla directory del file che contiene l'implementazione dell'attività personalizzata per aggiungere il **casella degli strumenti**e quindi fare clic su **Open**.  
  
4.  Fare clic su **OK** per completare l'aggiunta dell'attività alla casella degli strumenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dell'ActivityDesigner Legacy](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)