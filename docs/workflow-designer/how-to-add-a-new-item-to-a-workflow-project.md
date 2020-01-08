---
title: 'Progettazione flussi di lavoro: aggiungere un nuovo elemento al progetto flusso di lavoro'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7bedc36af2e8fbe19fbb3cc85d82be09d8673de
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593954"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro

Dopo aver creato un progetto flusso di lavoro, è possibile aggiungere al progetto attività del flusso di lavoro, finestre di progettazione e altri elementi comuni di Visual Studio.

Nella tabella seguente sono elencati gli elementi di Windows Workflow Foundation (WF) che è possibile aggiungere a un progetto flusso di lavoro:

| Name | Descrizione |
|-| - |
| Attività | Attività che deve essere composta da altre attività. Selezionando questo elemento viene aggiunto al progetto lo stesso file XAML ottenuto quando si seleziona il modello di **libreria attività** per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [creare un progetto di flusso di lavoro](creating-a-workflow-project.md). |
| Progettazione attività | Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello **libreria** ActivityDesigner per un nuovo progetto. |
| Attività Code | Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente. |
| Servizi del flusso di lavoro WCF | Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello di **applicazione del servizio flusso di lavoro WCF** per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [procedura: creare un'applicazione del servizio flusso di lavoro WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

   Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

1. Nel riquadro a sinistra selezionare la categoria flusso di **lavoro** e quindi selezionare un modello di elemento del flusso di lavoro.

   > [!NOTE]
   > Se la categoria flusso di **lavoro** non è visibile, installare prima di tutto il componente **Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Immettere un nome per l'elemento nella casella **nome** nella parte inferiore della finestra di dialogo.

1. Selezionare **Aggiungi** per aggiungere l'elemento al progetto.

## <a name="see-also"></a>Vedere anche

- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)
