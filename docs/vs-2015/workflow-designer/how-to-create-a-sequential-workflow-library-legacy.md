---
title: 'Procedura: creare una libreria flusso di lavoro sequenziale (Legacy) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 87ed4a11cf989e6b0b7804bcab728993b4a49050
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517685"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Procedura: creare una libreria del flusso di lavoro sequenziale (legacy)
Seguire questi passaggi per creare un progetto libreria flusso di lavoro sequenziale usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-library-project"></a>Per creare un progetto di libreria del flusso di lavoro sequenziale  
  
1.  Avviare Visual Studio.  
  
2.  Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3.  Selezionare il **.NET Framework 3.0** opzione o il **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere a progettazione legacy.  
  
    > [!NOTE]
    >  L'opzione predefinita nel [!INCLUDE[vs2010](../includes/vs2010-md.md)] viene **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.  
  
4.  Nel **tipi di progetto** riquadro, selezionare Visual c# o Visual Basic (sotto **Other Languages**) e quindi selezionare **flusso di lavoro**.  
  
5.  Nel **modelli** riquadro, selezionare **Sequential Workflow Library**.  
  
6.  Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
7.  Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
     Se si desidera una directory della soluzione creata per il progetto, selezionare la **Crea directory per soluzione** casella di controllo e immettere un nome nella **Nome soluzione** casella.  
  
8.  Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Stili di creazione del flusso di lavoro](http://msdn.microsoft.com/en-us/aacf4ec6-da05-4974-958a-974769dda739)