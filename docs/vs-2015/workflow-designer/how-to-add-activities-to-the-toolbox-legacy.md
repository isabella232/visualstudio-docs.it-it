---
title: 'Procedura: aggiungere attività alla casella degli strumenti (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656612"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procedura: aggiungere attività nella Casella degli strumenti [legacy]
Quando si compila una soluzione del flusso di lavoro con la legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)] che [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] fa riferimento [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] a o, le attività personalizzate possono essere aggiunte al progetto flusso di lavoro e alle finestre di progettazione inserite nella **casella degli strumenti** per semplificare l'accesso. È inoltre possibile aggiungere attività direttamente alla **casella degli strumenti** da una libreria di collegamento dinamico (dll).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Per aggiungere un'attività nella Casella degli strumenti da una DLL

1. Fare clic con il pulsante destro del mouse sull'area della finestra casella degli strumenti in **Windows Workflow**, quindi **scegliere Scegli elementi**.

2. Nella finestra di dialogo **Scegli elementi della casella degli strumenti** fare clic sulla scheda **componenti System. Activities** , quindi fare clic su **Sfoglia** dal lato inferiore destro della finestra.

3. Selezionare la DLL dalla directory di file che contiene l'implementazione dell'attività personalizzata da aggiungere alla **casella degli strumenti**, quindi fare clic su **Apri**.

4. Fare clic su **OK** per completare l'aggiunta dell'attività alla casella degli strumenti.

## <a name="see-also"></a>Vedere anche
 [Utilizzo delle](../workflow-designer/using-the-legacy-activity-designer.md) [attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md) di ActivityDesigner legacy