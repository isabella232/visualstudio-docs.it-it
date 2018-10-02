---
title: 'Procedura: aggiungere attività alla casella degli strumenti | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 66595a4aac8ae32c10223b30e6901decc630b10f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520188"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Procedura: aggiungere attività nella Casella degli strumenti
Le attività possono essere aggiunte per il **casella degli strumenti** nella soluzione in diversi modi. È possibile aggiungerli dall'interno il progetto corrente oppure fare riferimento a essi da un progetto diverso o da un assembly diverso.  
  
### <a name="to-add-an-activity-from-within-your-current-project"></a>Per aggiungere un'attività dall'interno del progetto corrente  
  
1.  Aggiungere una nuova attività personalizzata al progetto del flusso di lavoro corrente. [!INCLUDE[crabout](../includes/crabout-md.md)] aggiunta di una nuova attività personalizzata al progetto, vedere [procedura: aggiungere un nuovo elemento a un progetto di flusso di lavoro](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).  
  
2.  Aggiungere la logica personalizzata all'attività.  
  
3.  Compilare il progetto. Se la compilazione ha avuto esito positivo, una nuova categoria nella **casella degli strumenti** denominata "\<*nome progetto*>" viene visualizzato con l'attività personalizzata in essa inclusa.  
  
    > [!NOTE]
    >  Se la casella degli strumenti viene reimpostata, le attività personalizzate verranno rimosse, anche se la soluzione viene compilata nuovamente. Per ripopolare la casella degli strumenti con le attività personalizzate dopo che è stata reimpostata, riavviare [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  La casella degli strumenti può mostrare solo un'attività di un nome specificato. Se due attività derivanti da assembly differenti hanno lo stesso nome della classe, solo una viene visualizzata.  
  
    > [!NOTE]
    >  Il dominio applicazione viene condiviso tra le istanze dell'editor; se vengono usate le variabili statiche, queste verranno condivise anche tra le istanze dell'editor. Se non si tratta del comportamento desiderato, un servizio deve essere usato per tenere traccia delle istanze variabili. Visualizzare [utilizzando il contesto di modifica ModelItem](http://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) per informazioni sull'uso di servizi all'interno della finestra di progettazione.  
  
### <a name="to-add-an-activity-from-within-a-different-project"></a>Per aggiungere un'attività dall'interno di un altro progetto  
  
1.  Aprire una soluzione che contiene almeno un progetto flusso di lavoro e un progetto libreria attività personalizzato oppure un altro progetto flusso di lavoro che definisce un'attività personalizzata.  
  
2.  Compilare entrambi i progetti. Se la compilazione viene eseguita correttamente, una nuova categoria nella **casella degli strumenti** denominata "\<*nome progetto*>" viene visualizzato con l'attività personalizzata in essa inclusa.  
  
### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Per aggiungere un'attività alla Casella degli strumenti da un assembly  
  
1.  Aprire una soluzione per flussi di lavoro.  
  
2.  Dal **degli strumenti** dal menu **Scegli elementi della casella degli strumenti...** .  
  
3.  Nel **Scegli elementi della casella degli strumenti** finestra di dialogo, seleziona la **componenti System. Activities** scheda, quindi fare clic su **Sfoglia...** Per passare all'assembly che contiene l'attività personalizzata che si desidera aggiungere.  
  
4.  Selezionare l'assembly e fare clic su **OK**. Il componente attività personalizzata viene aggiunto all'elenco dei componenti e viene selezionato automaticamente.  
  
    1.  Fare clic su **OK** per chiudere la finestra di dialogo.  
  
5.  Per visualizzare la casella degli strumenti, selezionare **casella degli strumenti** dalle **visualizzazione** menu.  
  
6.  L'attività personalizzata viene visualizzato nei **casella degli strumenti** sotto la categoria che aveva lo stato attivo prima che l'elemento è stato aggiunto. Ad esempio, se il **generali** categoria è stata selezionata nella **della casella degli strumenti** prima di aggiungere l'elemento della casella degli strumenti, l'attività viene visualizzata sotto il **generale** categoria.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)