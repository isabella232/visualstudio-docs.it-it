---
title: 'Progettazione flussi di lavoro: Aggiungere un nuovo elemento al progetto del flusso di lavoro'
description: Informazioni su come aggiungere attività del flusso di lavoro, finestre di progettazione e altri elementi Visual Studio al progetto dopo aver creato un progetto del flusso di lavoro.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d09699c345878d27eecba518c54f8ff0cfd44d1b
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963524"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: Aggiungere un nuovo elemento a un progetto del flusso di lavoro

Dopo aver creato un progetto flusso di lavoro, è possibile aggiungere attività del flusso di lavoro, finestre di progettazione e altri elementi Visual Studio al progetto.

La tabella seguente elenca gli elementi Windows Workflow Foundation (WF) che è possibile aggiungere a un progetto del flusso di lavoro:

| Nome | Descrizione |
|-| - |
| Attività | Attività che deve essere composta da altre attività. La selezione di questo elemento aggiunge al progetto lo stesso file XAML ottenuto quando si seleziona il modello **Libreria** di attività per un nuovo progetto. Per altre informazioni su questa procedura, vedere Creare [un progetto flusso di lavoro](creating-a-workflow-project.md). |
| ActivityDesigner | Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Se si seleziona questo elemento, al progetto vengono aggiunti gli stessi file che si ottengono quando si seleziona il modello **Libreria di ActivityDesigner** per un nuovo progetto. |
| Attività Code | Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente. |
| Servizio flusso di lavoro WCF | Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato usando le attività del flusso di lavoro. Se si seleziona questo elemento, al progetto vengono aggiunti gli stessi file che si ottengono quando si seleziona il modello Applicazione servizio flusso di lavoro **WCF** per un nuovo progetto. Per altre informazioni su questa procedura, vedere [Procedura: Creare un'applicazione del servizio flusso di lavoro WCF](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

   Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento .

1. Nel riquadro a sinistra selezionare  la categoria Flusso di lavoro e quindi selezionare un modello di elemento del flusso di lavoro.

   > [!NOTE]
   > Se la categoria Flusso  di lavoro non è visualizzata, installare prima il **Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Installare Windows Workflow Foundation.](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)

1. Immettere un nome per l'elemento nella **casella Nome** nella parte inferiore della finestra di dialogo.

1. Selezionare **Aggiungi** per aggiungere l'elemento al progetto.

## <a name="see-also"></a>Vedi anche

- [Creare un progetto flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)
