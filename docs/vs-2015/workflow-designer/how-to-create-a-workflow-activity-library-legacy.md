---
title: 'Procedura: creare una libreria di attività del flusso di lavoro (legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604955"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Procedura: creare una libreria di attività del flusso di lavoro (legacy)
Seguire questi passaggi per creare un progetto libreria attività flussi di lavoro usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Per creare un progetto di raccolta di attività del flusso di lavoro

1. Avviare Visual Studio.

2. Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. Selezionare l'opzione **.NET Framework 3,0** o l'opzione **.NET Framework 3,5** nell'elenco a discesa nella parte superiore della finestra **nuovo progetto** per accedere alla finestra di progettazione legacy.

    > [!NOTE]
    > L'opzione predefinita in [!INCLUDE[vs2010](../includes/vs2010-md.md)] è **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.

4. Nel riquadro **Tipi progetto** selezionare Visual C# o Visual Basic (in **altri linguaggi**), quindi selezionare flusso di **lavoro**.

5. Nel riquadro **modelli** selezionare **libreria attività flusso di lavoro**.

6. Nella casella **nome** immettere un nome descrittivo per il progetto per facilitarne l'identificazione.

7. Nella casella **percorso** immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per passare a tale directory.

     Se si vuole creare una directory della soluzione per il progetto, selezionare la casella **di controllo Crea directory per soluzione** e immettere un nome nella casella **Nome soluzione** .

8. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 [Creazione di progetti flusso di lavoro legacy](../workflow-designer/creating-legacy-workflow-projects.md) [mediante le](../workflow-designer/using-the-legacy-activity-designer.md) [attività del flusso di lavoro](../workflow-designer/legacy-workflow-activities.md) legacy di ActivityDesigner legacy [sviluppo di attività flusso di lavoro](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) [Windows Workflow Foundation attività](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)