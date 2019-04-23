---
title: 'Procedura: Creare una libreria del flusso di lavoro macchina a stati (Legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ca54c1585d683745bb42815921f3982c9c0fd441
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084895"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Procedura: Creare una libreria del flusso di lavoro di una macchina a stati (legacy)
Seguire questi passaggi per creare un progetto libreria flusso di lavoro di una macchina a stati usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>Procedura: creazione di un progetto di libreria del flusso di lavoro di una macchina a stati   
  
1. Avviare Visual Studio.  
  
2. Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3. Selezionare il **.NET Framework 3.0** opzione o il **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere a progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita nel [!INCLUDE[vs2010](../includes/vs2010-md.md)] viene **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.  
  
4. Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **Other Languages**) e quindi selezionare **flusso di lavoro**.  
  
5. Nel **modelli** riquadro, selezionare **libreria del flusso di lavoro macchina a stati**.  
  
6. Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
7. Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
     Se si desidera una directory della soluzione creata per il progetto, selezionare la **Crea directory per soluzione** casella di controllo e immettere un nome nella **Nome soluzione** casella.  
  
8. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Flussi di lavoro della macchina a stati](http://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d)