---
title: Creare un progetto di Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0856ff93beef602d02defb58f90f69898a121f2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943353"
---
# <a name="workflow-project-templates"></a>Modelli di progetto del flusso di lavoro

È possibile creare flussi di lavoro, servizi flusso di lavoro Windows Communication Foundation (WCF), le attività personalizzate e ActivityDesigner personalizzati usando i modelli di progetto di Visual Studio. Questo articolo descrive come creare applicazioni e librerie con i modelli di progetto disponibili in Visual Studio.

## <a name="create-a-workflow-project"></a>Creare un progetto flusso di lavoro

Visual Studio offre quattro diversi modelli di progetto del flusso di lavoro:

- App di console del flusso di lavoro

- App del servizio del flusso di lavoro WCF

- Libreria di attività

- Libreria ActivityDesigner

Per accedere a questi modelli, prima di tutto installare il **Windows Workflow Foundation** componente di Visual Studio 2017. Per istruzioni dettagliate, vedere [installazione di Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Dopo aver installato il **Windows Workflow Foundation** componente, aprire il **nuovo progetto** finestra di dialogo selezionando **File** > **New**  >  **Progetto**.

1. Nel riquadro di sinistra, selezionare la **Visual c#** > **flusso di lavoro** categoria (o **Visual Basic** > **flusso di lavoro**se si preferisce Visual Basic).

1. Nel riquadro centrale, selezionare un modello di progetto, ad esempio **applicazione Console flusso di lavoro**.

1. Nel **nome** immettere un nome descrittivo per il progetto affinché sia facilmente identificabile.

1. Nel **posizione** casella, immettere la directory in cui si desidera salvare il progetto o selezionare **Sfoglia** per spostarsi su di esso.

1. Nel **soluzione** immettere il nome per la nuova soluzione. Selezionare **OK** per creare l'applicazione.

   > [!NOTE]
   > Se si desidera aggiungere un nuovo progetto a una soluzione esistente, aprire la soluzione in Visual Studio, fare doppio clic la soluzione in **Esplora soluzioni**e selezionare **Add** > **New Project** per aprire la **nuovo progetto** nella finestra di dialogo.

## <a name="workflow-console-app"></a>App di console del flusso di lavoro

Se si sceglie la **applicazione Console flusso di lavoro** modello, Visual Studio crea una definizione del flusso di lavoro in XAML. La finestra di progettazione del flusso di lavoro si apre e visualizza l'area di disegno del flusso di lavoro che è stato creato. Per creare un flusso di lavoro, trascinare attività o altri elementi del flusso di lavoro dalla **casella degli strumenti** all'area di progettazione.

## <a name="wcf-workflow-service-app"></a>App del servizio del flusso di lavoro WCF

Se si sceglie la **applicazione del servizio del flusso di lavoro WCF** modello, Visual Studio crea una definizione del servizio come XAML. Verrà visualizzata la finestra di progettazione del flusso di lavoro per la visualizzazione di progettazione con una <xref:System.Activities.Statements.Sequence> che contiene un set di attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> attività.

## <a name="activity-library"></a>Libreria di attività

Se si sceglie la **libreria di attività** modello, Visual Studio crea una definizione di attività in XAML. Finestra di progettazione del flusso di lavoro si apre e visualizza l'area di disegno per l'attività personalizzata. Trascinare un'attività dalla **casella degli strumenti** all'area di progettazione per includerla nell'attività personalizzata.

> [!NOTE]
> Si è consentita una sola attività figlio nel corpo dell'attività personalizzata. Tuttavia, tale attività figlio può essere un'attività composta, ad esempio un <xref:System.Activities.Statements.Sequence> attività o <xref:System.Activities.Statements.Flowchart> attività.

## <a name="activity-designer-library"></a>Libreria ActivityDesigner

Se si sceglie la **libreria ActivityDesigner** modello, Visual Studio crea una definizione dell'ActivityDesigner in un file di implementazione code-behind e XAML. La finestra di progettazione del flusso di lavoro apre e visualizza l'area di disegno per l'ActivityDesigner. Trascinare Windows Presentation Foundation (WPF) dei controlli **casella degli strumenti** all'area di progettazione per usarli nell'ActivityDesigner personalizzati.

Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [come: Creare un ActivityDesigner personalizzato](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Gli ActivityDesigner personalizzati sono utilizzabile per le attività personalizzate e per attività predefinite di .NET Framework.

## <a name="see-also"></a>Vedere anche

- [Utilizzare la finestra di progettazione del flusso di lavoro](developing-applications-with-the-workflow-designer.md)
- [Progettazione flussi di lavoro (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)