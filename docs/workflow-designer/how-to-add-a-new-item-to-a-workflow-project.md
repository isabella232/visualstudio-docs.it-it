---
title: 'Finestra di progettazione del flusso di lavoro - procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0aa2be7fd8ecccbd8de0aa54c2693dd6b02c7e10
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971644"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: aggiungere un nuovo elemento ad un progetto flusso di lavoro

Dopo aver creato un progetto flusso di lavoro, è possibile aggiungere le attività del flusso di lavoro, finestre di progettazione e altri elementi di Visual Studio comuni al progetto.

Nella tabella seguente vengono elencati gli elementi di Windows Workflow Foundation (WF) che è possibile aggiungere a un progetto flusso di lavoro.

|nome|Descrizione|
|----------|-----------------|
|Attività|Attività che deve essere composta da altre attività. Selezionando questo elemento viene aggiunto lo stesso file XAML al progetto ottenuti quando si seleziona il **libreria attività** modello per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [procedura: creare una libreria attività](../workflow-designer/how-to-create-an-activity-library.md).|
|ActivityDesigner|Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento consente di aggiungere gli stessi file al progetto ottenuti quando si seleziona il **libreria ActivityDesigner** modello per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [procedura: creare una libreria ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md).|
|Attività Code|Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente.|
|Servizio flusso di lavoro WCF|Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento consente di aggiungere gli stessi file al progetto ottenuti quando si seleziona il **applicazione del servizio del flusso di lavoro WCF** modello per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [procedura: creare un'applicazione di servizio del flusso di lavoro WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md).|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1.  Nel **progetto** menu, fare clic su **Aggiungi nuovo elemento...** .

     Il **aggiungere un nuovo elemento** verrà visualizzata la finestra di dialogo.

2.  Nel **modelli installati** riquadro, selezionare **flusso di lavoro** gruppo.

3.  Selezionare uno dei quattro elementi. Nella tabella precedente sono elencate le selezioni disponibili.

4.  Digitare un nome appropriato per la voce di **nome** nella parte inferiore della finestra di dialogo.

5.  Fare clic su **Aggiungi** ad aggiungere l'elemento al progetto flusso di lavoro corrente.

## <a name="see-also"></a>Vedere anche

- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)