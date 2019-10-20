---
title: 'Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656624"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: aggiungere un nuovo elemento ad un progetto flusso di lavoro
Dopo aver creato un progetto flusso di lavoro, è possibile aggiungervi attività del flusso di lavoro, finestre di progettazione e altri elementi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comuni.

 Nella tabella seguente sono elencati gli elementi [!INCLUDE[wf](../includes/wf-md.md)] che è possibile aggiungere a un progetto flusso di lavoro.

|Name|Descrizione|
|----------|-----------------|
|Attività|Attività che deve essere composta da altre attività. Selezionando questo elemento viene aggiunto al progetto lo stesso file XAML ottenuto quando si seleziona il modello di **libreria attività** per un nuovo progetto. [!INCLUDE[crabout](../includes/crabout-md.md)] su questa procedura, vedere [procedura: creare una libreria di attività](../workflow-designer/how-to-create-an-activity-library.md).|
|ActivityDesigner|Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello **libreria** ActivityDesigner per un nuovo progetto. [!INCLUDE[crabout](../includes/crabout-md.md)] su questa procedura, vedere [procedura: creare una libreria di](../workflow-designer/how-to-create-an-activity-designer-library.md)ActivityDesigner.|
|Attività Code|Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente.|
|Servizio flusso di lavoro WCF|Servizio [!INCLUDE[indigo2](../includes/indigo2-md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello di **applicazione del servizio flusso di lavoro WCF** per un nuovo progetto. [!INCLUDE[crabout](../includes/crabout-md.md)] su questa procedura, vedere [procedura: creare un'applicazione del servizio flusso di lavoro WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Scegliere **Aggiungi nuovo elemento**dal menu **progetto** .

     Verrà visualizzata la finestra **di dialogo Aggiungi nuovo elemento** .

2. Nel riquadro **modelli installati** selezionare gruppo di **flussi di lavoro** .

3. Selezionare uno dei quattro elementi. Nella tabella precedente sono elencate le selezioni disponibili.

4. Digitare un nome appropriato per l'elemento nella casella **nome** nella parte inferiore della finestra di dialogo.

5. Fare clic su **Aggiungi** per aggiungere l'elemento al progetto flusso di lavoro corrente.

## <a name="see-also"></a>Vedere anche
 [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)