---
title: "Procedura: Creare un'applicazione di servizio del flusso di lavoro WCF | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0c258ea081e95179c507f76413ae2a5fc7d71a5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705844"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Procedura: Creare un'applicazione del servizio flusso di lavoro WCF
Le applicazioni di servizi flusso di lavoro di [!INCLUDE[indigo1](../includes/indigo1-md.md)] sono servizi di comunicazioni distribuite che scambiano messaggi con i client oltre i limiti dei processi. L'implementazione del contratto di servizio sul lato servizio viene eseguita in modo dichiarativo tramite le attività del flusso di lavoro [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] in modo analogo ai servizi flusso di lavoro legacy di .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Per creare un'applicazione di servizi flusso di lavoro WCF  
  
1. Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Nel **File** dal menu **New**, quindi selezionare **progetto...** .  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3. Nel **modelli installati** riquadro, selezionare **WCF** oppure **flusso di lavoro** da una il **Visual c#** o **Visual Basic** a seconda del linguaggio scelto.  
  
4. Nel riquadro centrale, selezionare **applicazione del servizio del flusso di lavoro WCF**.  
  
5. Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
6. Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
7. Nel **soluzione** casella, selezionare questa opzione per creare una nuova soluzione e quindi fare clic su **OK**.  
  
    > [!NOTE]
    > Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)], fare clic con il pulsante destro la soluzione in **Esplora soluzioni**e selezionare **Add**, quindi  **Nuovo progetto...** Per aprire la **nuovo progetto** nella finestra di dialogo. Procedere come descritto sopra in questa procedura.  
  
8. Il modello di progetto crea una definizione di servizio come XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] viene aperto sulla visualizzazione Progettazione con un'attività <xref:System.Activities.Statements.Sequence> che contiene un set di attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare un'attività](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)