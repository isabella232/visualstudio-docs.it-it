---
title: 'Finestra di progettazione del flusso di lavoro - procedura: Aggiungere un nuovo elemento a un progetto flusso di lavoro'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f0fb6c013e3df041e750344c09fb19f8c43b254
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649589"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: Aggiungere un nuovo elemento a un progetto di flusso di lavoro

Dopo aver creato un progetto di flusso di lavoro, è possibile aggiungere attività del flusso di lavoro, finestre di progettazione e altri elementi di Visual Studio comuni al progetto.

La tabella seguente elenca gli elementi Windows Workflow Foundation (WF) che è possibile aggiungere a un progetto di flusso di lavoro:

| Nome | Descrizione |
|-| - |
| Attività | Attività che deve essere composta da altre attività. Selezionando questo elemento vengono aggiunti nello stesso file XAML al progetto ottenuti quando si seleziona il **libreria di attività** modello per un nuovo progetto. Per altre informazioni su questa procedura, vedere [creare un progetto di flusso di lavoro](creating-a-workflow-project.md). |
| ActivityDesigner | Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento vengono aggiunti gli stessi file al progetto ottenuto quando si seleziona il **libreria ActivityDesigner** modello per un nuovo progetto. |
| Attività Code | Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente. |
| Servizio flusso di lavoro WCF | Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento vengono aggiunti gli stessi file al progetto ottenuto quando si seleziona il **applicazione del servizio del flusso di lavoro WCF** modello per un nuovo progetto. Per altre informazioni su questa procedura, vedere [come: Creare un'applicazione di servizio del flusso di lavoro WCF](/visualstudio/workflow-designer/creating-a-workflow-project). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

   Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

1. Nel riquadro di sinistra, selezionare la **flusso di lavoro** categoria e quindi selezionare un modello di elemento del flusso di lavoro.

   > [!NOTE]
   > Se non viene visualizzato il **flusso di lavoro** category, installare prima il **Windows Workflow Foundation** componente di Visual Studio. Per istruzioni dettagliate, vedere [installazione di Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Immettere un nome per l'elemento nel **nome** nella parte inferiore della finestra di dialogo.

1. Selezionare **Add** per aggiungere l'elemento al progetto.

## <a name="see-also"></a>Vedere anche

- [Creare un progetto di flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)