---
title: "Procedura: Creare un'applicazione Console flusso di lavoro | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 33666c0e5d63d8d4d33d544fcfe18d8c185ce843
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044352"
---
# <a name="how-to-create-a-workflow-console-application"></a>Procedura: Creare un'applicazione console flusso di lavoro
[!INCLUDE[wf](../includes/wf-md.md)] consente di creare flussi di lavoro per l'esecuzione di processi di utenti o di sistema. [!INCLUDE[wfd1](../includes/wfd1-md.md)] fornisce l'area di progettazione per la creazione di tali flussi. La [!INCLUDE[wfd2](../includes/wfd2-md.md)] può essere usata per creare flussi di lavoro dall'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o può essere integrata in altre applicazioni che riallocano la finestra di progettazione.  
  
 In questo argomento viene descritto come usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] in [!INCLUDE[vs2010](../includes/vs2010-md.md)] per creare un flusso di lavoro in un'applicazione console.  
  
### <a name="to-create-a-workflow-console-application"></a>Per creare un'applicazione console flusso di lavoro  
  
1. Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2. Nel **File** dal menu **New**, quindi selezionare **progetto...** .  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
3. Nel **modelli installati** riquadro, selezionare **flusso di lavoro** dal **Visual c#** o **Visual Basic** raggruppamenti, a seconda di lingua di preferenza.  
  
4. Nel riquadro centrale, selezionare **applicazione Console flusso di lavoro**.  
  
5. Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
6. Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
7. Nel **soluzione** immettere il nome per la nuova soluzione. Fare clic su **OK** per creare l'applicazione.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)], fare clic con il pulsante destro la soluzione in **Esplora soluzioni**e selezionare **Add**, quindi  **Nuovo progetto...** Per aprire la **nuovo progetto** nella finestra di dialogo. Procedere come descritto sopra in questa procedura.  
  
8. Il modello di progetto crea una definizione del flusso di lavoro in XAML mentre la definizione dell'applicazione console è in codice sorgente. In [!INCLUDE[wfd2](../includes/wfd2-md.md)] verrà visualizzata l'area di disegno per il flusso di lavoro creato.  
  
9. Per creare un flusso di lavoro, trascinare attività o altri elementi del flusso di lavoro dal **casella degli strumenti** all'area di progettazione del flusso di lavoro.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)