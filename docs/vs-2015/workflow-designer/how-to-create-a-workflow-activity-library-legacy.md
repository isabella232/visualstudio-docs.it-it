---
title: 'Procedura: Creare una libreria di attività del flusso di lavoro (Legacy) | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9baa358c3728c6cbedc5f8768b29ba7efe64b399
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703285"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Procedura: Creare una libreria di attività del flusso di lavoro (legacy)
Seguire questi passaggi per creare un progetto libreria attività flussi di lavoro usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-workflow-activity-library-project"></a>Per creare un progetto di raccolta di attività del flusso di lavoro  
  
1. Avviare Visual Studio.  
  
2. Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3. Selezionare il **.NET Framework 3.0** opzione o il **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere a progettazione legacy.  
  
    > [!NOTE]
    > L'opzione predefinita nel [!INCLUDE[vs2010](../includes/vs2010-md.md)] viene **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.  
  
4. Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **Other Languages**) e quindi selezionare **flusso di lavoro**.  
  
5. Nel **modelli** riquadro, selezionare **Workflow Activity Library**.  
  
6. Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
7. Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
     Se si desidera una directory della soluzione creata per il progetto, selezionare la **Crea directory per soluzione** casella di controllo e immettere un nome nella **Nome soluzione** casella.  
  
8. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Utilizzo dell'ActivityDesigner Legacy](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Attività flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)   
 [Sviluppo di attività del flusso di lavoro](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52)   
 [Attività di Windows Workflow Foundation](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)