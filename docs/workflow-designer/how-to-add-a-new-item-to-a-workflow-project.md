---
title: 'Progettazione flussi di lavoro: aggiungere un nuovo elemento al progetto flusso di lavoro'
description: Informazioni su come aggiungere attività del flusso di lavoro, finestre di progettazione e altri elementi comuni di Visual Studio al progetto dopo aver creato un progetto flusso di lavoro.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e0cc4b24462583a5f704f47c16e6e8d30456512b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938460"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: aggiungere un nuovo elemento a un progetto flusso di lavoro

Dopo aver creato un progetto flusso di lavoro, è possibile aggiungere al progetto attività del flusso di lavoro, finestre di progettazione e altri elementi comuni di Visual Studio.

Nella tabella seguente sono elencati gli elementi di Windows Workflow Foundation (WF) che è possibile aggiungere a un progetto flusso di lavoro:

| Nome | Descrizione |
|-| - |
| Attività | Attività che deve essere composta da altre attività. Selezionando questo elemento viene aggiunto al progetto lo stesso file XAML ottenuto quando si seleziona il modello di **libreria attività** per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [creare un progetto di flusso di lavoro](creating-a-workflow-project.md). |
| ActivityDesigner | Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello **libreria** ActivityDesigner per un nuovo progetto. |
| Attività Code | Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente. |
| Servizio flusso di lavoro WCF | Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento vengono aggiunti al progetto gli stessi file ottenuti quando si seleziona il modello di **applicazione del servizio flusso di lavoro WCF** per un nuovo progetto. Per ulteriori informazioni su questa procedura, vedere [procedura: creare un'applicazione del servizio flusso di lavoro WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

   Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

1. Nel riquadro a sinistra selezionare la categoria flusso di **lavoro** e quindi selezionare un modello di elemento del flusso di lavoro.

   > [!NOTE]
   > Se la categoria flusso di **lavoro** non è visibile, installare prima di tutto il componente **Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Immettere un nome per l'elemento nella casella **nome** nella parte inferiore della finestra di dialogo.

1. Selezionare **Aggiungi** per aggiungere l'elemento al progetto.

## <a name="see-also"></a>Vedi anche

- [Creazione di un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)
