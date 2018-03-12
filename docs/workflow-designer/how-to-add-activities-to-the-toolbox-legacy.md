---
title: "Procedura: aggiungere attività alla casella degli strumenti (Legacy) | Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d6d7e817ae34b3e39d617ad5d12802cabd5cedc
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procedura: aggiungere attività nella Casella degli strumenti [legacy]
Quando si compila una soluzione del flusso di lavoro con Progettazione flussi di lavoro Windows legacy che fa riferimento il [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], le attività personalizzate possono essere aggiunti al progetto flusso di lavoro e agli ActivityDesigner disponibili nella **della casella degli strumenti** per facilità di accesso. È inoltre possibile aggiungere le attività direttamente il **della casella degli strumenti** da una libreria di collegamento dinamico (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Per aggiungere un'attività nella Casella degli strumenti da una DLL

1.  Il pulsante destro della casella degli strumenti finestra sotto **Windows Workflow**, quindi fare clic su **Scegli elementi**.

2.  Nel **Scegli elementi della casella degli strumenti** nella finestra di dialogo fare clic su di **componenti System. Activities** scheda e quindi fare clic su **Sfoglia** dal lato inferiore destro della finestra.

3.  Selezionare la DLL dalla directory del file che contiene l'implementazione dell'attività personalizzata per aggiungere il **della casella degli strumenti**, quindi fare clic su **aprire**.

4.  Fare clic su **OK** per completare l'aggiunta dell'attività nella casella degli strumenti.

## <a name="see-also"></a>Vedere anche

- [Uso dell'Activity Designer legacy](../workflow-designer/using-the-legacy-activity-designer.md)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)