---
title: 'Finestra di progettazione del flusso di lavoro - procedura: aggiungere un nuovo elemento a un progetto di flusso di lavoro'
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbed404f2cdd69446d8945fc9ff96703eccd161f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814232"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Procedura: aggiungere un nuovo elemento a un progetto di flusso di lavoro

Dopo aver creato un progetto di flusso di lavoro, è possibile aggiungere attività del flusso di lavoro, finestre di progettazione e altri elementi di Visual Studio comuni al progetto.

La tabella seguente elenca gli elementi Windows Workflow Foundation (WF) che è possibile aggiungere a un progetto di flusso di lavoro:


| nome | Descrizione |
|-| - |
| Attività | Attività che deve essere composta da altre attività. Selezionando questo elemento vengono aggiunti nello stesso file XAML al progetto ottenuti quando si seleziona il **libreria di attività** modello per un nuovo progetto. Per altre informazioni su questa procedura, vedere [procedura: creare una libreria attività](../workflow-designer/how-to-create-an-activity-library.md). |
| ActivityDesigner | Finestra di progettazione per personalizzare l'esperienza di progettazione di un'attività. Selezionando questo elemento vengono aggiunti gli stessi file al progetto ottenuto quando si seleziona il **libreria ActivityDesigner** modello per un nuovo progetto. Per altre informazioni su questa procedura, vedere [procedura: creare una libreria ActivityDesigner](../workflow-designer/how-to-create-an-activity-designer-library.md). |
| Attività Code | Attività con la logica di esecuzione scritta nel codice. Un file di codice sorgente con un override del metodo <xref:System.Activities.CodeActivity.Execute%2A> è già generato automaticamente. |
| Servizio flusso di lavoro WCF | Servizio [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] compilato usando le attività del flusso di lavoro. Selezionando questo elemento vengono aggiunti gli stessi file al progetto ottenuto quando si seleziona il **applicazione del servizio del flusso di lavoro WCF** modello per un nuovo progetto. Per altre informazioni su questa procedura, vedere [procedura: creare un'applicazione di servizio del flusso di lavoro WCF](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Per aggiungere un nuovo elemento a un progetto flusso di lavoro

1. Nel **Project** dal menu **Aggiungi nuovo elemento**.

   Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

1. Nel riquadro di sinistra, selezionare la **flusso di lavoro** categoria e quindi selezionare un modello di elemento del flusso di lavoro.

   > [!NOTE]
   > Se non viene visualizzato il **flusso di lavoro** category, installare prima il **Windows Workflow Foundation** componente di Visual Studio 2017. Per istruzioni dettagliate, vedere [installazione di Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Immettere un nome per l'elemento nel **nome** nella parte inferiore della finestra di dialogo.

1. Selezionare **Add** per aggiungere l'elemento al progetto.

## <a name="see-also"></a>Vedere anche

- [Creare un progetto di flusso di lavoro](../workflow-designer/creating-a-workflow-project.md)