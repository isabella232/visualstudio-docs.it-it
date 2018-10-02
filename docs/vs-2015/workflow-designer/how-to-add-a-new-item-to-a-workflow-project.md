---
title: 'Procedura: aggiungere un nuovo elemento a un progetto di flusso di lavoro | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1779fa4f3f644913bfe39164e707dfee4673502b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519980"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: aggiungere un nuovo elemento ad un progetto flusso di lavoro
Dopo aver creato un progetto flusso di lavoro, è possibile aggiungervi attività del flusso di lavoro, finestre di progettazione e altri elementi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comuni.  
  
 Nella tabella seguente sono elencati gli elementi [!INCLUDE[wf](../includes/wf-md.md)] che è possibile aggiungere a un progetto flusso di lavoro.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|Attività|Attività che deve essere composta da altre attività. Selezionando questo elemento vengono aggiunti nello stesso file XAML al progetto ottenuti quando si seleziona il **libreria di attività** modello per un nuovo progetto. [!INCLUDE[crabout](../includes/crabout-md.md)] Questa procedura, vedere [procedura: creare una libreria attività](../workflow-designer/how-to-create-an-activity-library.md).|  
|ActivityDesigner|Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento vengono aggiunti gli stessi file al progetto ottenuto quando si seleziona il **libreria ActivityDesigner** modello per un nuovo progetto. [!INCLUDE[crabout](../includes/crabout-md.md)] Questa procedura, vedere [procedura: creare una libreria ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|  
|Attività Code|Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente.|  
|Servizio flusso di lavoro WCF|Servizio [!INCLUDE[indigo2](../includes/indigo2-md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento vengono aggiunti gli stessi file al progetto ottenuto quando si seleziona il **applicazione del servizio del flusso di lavoro WCF** modello per un nuovo progetto. [!INCLUDE[crabout](../includes/crabout-md.md)] Questa procedura, vedere [procedura: creare un'applicazione di servizio del flusso di lavoro WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|  
  
### <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro  
  
1.  Nel **Project** menu, fare clic su **Aggiungi nuovo elemento...** .  
  
     Il **aggiungere un nuovo elemento** verrà visualizzata la finestra di dialogo.  
  
2.  Nel **modelli installati** riquadro, selezionare **flusso di lavoro** gruppo.  
  
3.  Selezionare uno dei quattro elementi. Nella tabella precedente sono elencate le selezioni disponibili.  
  
4.  Digitare un nome appropriato per l'elemento nel **nome** nella parte inferiore della finestra di dialogo.  
  
5.  Fare clic su **Add** per aggiungere l'elemento al progetto del flusso di lavoro corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)