---
title: 'Procedura: Creare applicazioni Console flusso di lavoro sequenziale (Legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 932b770f38f75d26028eceb6c0addc2ababeef6d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696353"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procedura: Creare applicazioni console flusso di lavoro sequenziali (legacy)
Seguire questi passaggi per creare un progetto Applicazione console flusso di lavoro sequenziale usando la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy fornita da [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Creazione delle Applicazioni console del flusso di lavoro sequenziale  
  
1. Avviare Visual Studio.  
  
2. Nel menu **File** scegliere **Nuovo** e quindi selezionare **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3. Selezionare il **.NET Framework 3.0** opzione o il **.NET Framework 3.5** opzione nella casella di riepilogo nella parte superiore del **nuovo progetto** finestra per accedere a progettazione legacy.  
  
    > [!NOTE]
    > L'opzione predefinita nel [!INCLUDE[vs2010](../includes/vs2010-md.md)] viene **.NET Framework 4**. Questa opzione viene usata per creare applicazioni [!INCLUDE[wf](../includes/wf-md.md)] che vengono destinate a [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] e non usa la finestra di progettazione legacy.  
  
4. Nel **tipi di progetto** riquadro, selezionare progetti Visual c# o progetti Visual Basic (sotto **Other Languages**) e quindi selezionare **flusso di lavoro**.  
  
5. Nel **modelli** riquadro, selezionare **applicazione Console flusso di lavoro sequenziale**.  
  
6. Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
7. Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
     Verrà aperta la finestra di progettazione Windows Forms nella quale verrà visualizzato il Form1 del progetto creato.  
  
8. Fare clic su **OK**.  
  
     Verrà aperta la finestra di Progettazione flussi di lavoro e verrà visualizzata l'area di progettazione del flusso di lavoro sequenziale creato.  
  
9. Trascinare un'attività dal **casella degli strumenti** all'area di progettazione nel **rilasciare l'attività** area designata.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di progetti di flusso di lavoro Legacy](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Sviluppo di flussi di lavoro](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)