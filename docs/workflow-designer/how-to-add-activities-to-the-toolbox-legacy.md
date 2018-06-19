---
title: 'Finestra di progettazione del flusso di lavoro - procedura: aggiungere attività alla casella degli strumenti (Legacy)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969427"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procedura: aggiungere attività nella Casella degli strumenti [legacy]

Quando si compila una soluzione del flusso di lavoro con Progettazione flussi di lavoro Windows legacy destinato a .NET Framework versione 3.5 o la WinFX, le attività personalizzate possono essere aggiunti al progetto del flusso di lavoro e agli ActivityDesigner nel **casella degli strumenti** per facilità di accesso. È inoltre possibile aggiungere le attività direttamente il **della casella degli strumenti** da una libreria di collegamento dinamico (DLL).

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Per aggiungere un'attività nella Casella degli strumenti da una DLL

1.  Il pulsante destro della casella degli strumenti finestra sotto **Windows Workflow**, quindi fare clic su **Scegli elementi**.

2.  Nel **Scegli elementi della casella degli strumenti** nella finestra di dialogo fare clic su di **componenti System. Activities** scheda e quindi fare clic su **Sfoglia** dal lato inferiore destro della finestra.

3.  Selezionare la DLL dalla directory del file che contiene l'implementazione dell'attività personalizzata per aggiungere il **della casella degli strumenti**, quindi fare clic su **aprire**.

4.  Fare clic su **OK** per completare l'aggiunta dell'attività nella casella degli strumenti.

## <a name="see-also"></a>Vedere anche

- [Uso dell'Activity Designer legacy](../workflow-designer/using-the-legacy-activity-designer.md)
- [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)