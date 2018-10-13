---
title: 'Procedura: creare una libreria Activity Designer | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6802f92f349d15d48935f4e7c3db85abf7c12535
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258271"
---
# <a name="how-to-create-an-activity-designer-library"></a>Procedura: creare una libreria ActivityDesigner
Gli ActivityDesigner personalizzati consentono di creare un'interfaccia utente per un'attività personalizzata o standard. È possibile controllare la complessità dell'interfaccia utente e creare più ActivityDesigner per un'attività. Questo scenario consente di creare finestre di progettazione personalizzate per diversi destinatari.  
  
### <a name="to-create-an-activity-designer-library"></a>Per creare una libreria ActivityDesigner  
  
1.  Avviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Nel **File** dal menu **New**, quindi selezionare **progetto...** Per aprire la **nuovo progetto** nella finestra di dialogo.  
  
3.  Nel **tipi di progetto** riquadro, selezionare **flusso di lavoro** da una il **Visual c#** oppure **Visual Basic** a seconda la voce preferita lingua.  
  
4.  Nel **modelli** riquadro, selezionare **libreria ActivityDesigner**.  
  
5.  Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.  
  
6.  Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto oppure fare clic su **Sfoglia** per spostarsi su di esso.  
  
7.  Nel **soluzione** casella, digitare un nome descrittivo per la soluzione, quindi fare clic su **OK**.  
  
    > [!NOTE]
    >  Se si desidera aggiungere un'applicazione console flusso di lavoro a una soluzione esistente, aprire la soluzione in [!INCLUDE[vs2010](../includes/vs2010-md.md)], fare clic con il pulsante destro sulla soluzione in **Esplora soluzioni**e selezionare **Add**, quindi **Nuovo progetto...** Per aprire la **nuovo progetto** nella finestra di dialogo. Procedere come descritto sopra in questa procedura.  
  
8.  Il modello di progetto crea una definizione dell'ActivityDesigner in XAML mentre il file di implementazione code-behind è in codice sorgente. [!INCLUDE[wfd1](../includes/wfd1-md.md)] verrà visualizzato con l'area di disegno per l'ActivityDesigner.  
  
9. Trascinare [!INCLUDE[avalon1](../includes/avalon1-md.md)] dei controlli il **casella degli strumenti** all'area di progettazione per usarli nell'ActivityDesigner personalizzati.  Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [procedura: creare un ActivityDesigner personalizzato](http://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).  
  
    > [!WARNING]
    >  Gli ActivityDesigner personalizzati possono essere usati per le attività personalizzate nonché per impostazione predefinita [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)