---
title: Creare un progetto di Workflow Foundation
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f793e6ff468bdec6df499c5e5eb6b8524e9e4d5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650568"
---
# <a name="workflow-project-templates"></a>Modelli di progetto flusso di lavoro

È possibile creare flussi di lavoro, Windows Communication Foundation (WCF) servizi flusso di lavoro, attività personalizzate e ActivityDesigner personalizzati usando i modelli di progetto di Visual Studio. Questo articolo descrive come creare librerie e applicazioni con i modelli di progetto disponibili in Visual Studio.

## <a name="create-a-workflow-project"></a>Creare un progetto flusso di lavoro

Visual Studio fornisce quattro diversi modelli di progetto del flusso di lavoro:

- App console flusso di lavoro

- App del servizio flusso di lavoro WCF

- Libreria attività

- Libreria ActivityDesigner

Per accedere a questi modelli, installare prima il componente **Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Dopo aver installato il componente **Windows Workflow Foundation** , selezionare **File**  > **nuovo**  > **progetto**.

1. Cercare e selezionare un modello di progetto flusso di lavoro, ad esempio il modello **applicazione console flusso** di lavoro.

1. Continuare con per creare il progetto.

   > [!NOTE]
   > Se si desidera aggiungere un nuovo progetto a una soluzione esistente, aprire la soluzione in Visual Studio, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni**e selezionare **Aggiungi**  > **nuovo progetto**.

## <a name="workflow-console-app"></a>App console flusso di lavoro

Se si sceglie il modello **applicazione console flusso di lavoro** , Visual Studio crea una definizione del flusso di lavoro in XAML. Viene aperto il Progettazione flussi di lavoro e viene visualizzata l'area di disegno per il flusso di lavoro creato. Per comporre un flusso di lavoro, trascinare le attività o altri elementi del flusso di lavoro dalla **casella degli strumenti** all'area di progettazione.

## <a name="wcf-workflow-service-app"></a>App del servizio flusso di lavoro WCF

Se si sceglie il modello **applicazione del servizio flusso di lavoro WCF** , Visual Studio crea una definizione di servizio come XAML. Il Progettazione flussi di lavoro viene aperto nella visualizzazione progettazione con un'attività <xref:System.Activities.Statements.Sequence> contenente un set di attività di <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>.

## <a name="activity-library"></a>Libreria attività

Se si sceglie il modello di **libreria di attività** , Visual Studio crea una definizione di attività in XAML. Progettazione flussi di lavoro viene aperto e viene visualizzata l'area di disegno per l'attività personalizzata. Trascinare un'attività dalla **casella degli strumenti** nell'area di progettazione per includerla nell'attività personalizzata.

> [!NOTE]
> Si è consentita una sola attività figlio nel corpo dell'attività personalizzata. Tuttavia, tale attività figlio potrebbe essere un'attività composita, ad esempio un'attività <xref:System.Activities.Statements.Sequence> o un'attività <xref:System.Activities.Statements.Flowchart>.

## <a name="activity-designer-library"></a>Libreria ActivityDesigner

Se si sceglie il modello **libreria** ActivityDesigner, Visual Studio crea una definizione di ACTIVITYDESIGNER in XAML e un file di implementazione code-behind. Viene aperto il Progettazione flussi di lavoro e viene visualizzata l'area di disegno per l'ActivityDesigner. Trascinare i controlli Windows Presentation Foundation (WPF) dalla **casella degli strumenti** nell'area di progettazione per utilizzarli nell'ActivityDesigner personalizzato.

Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [procedura: creare un ActivityDesigner personalizzato](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

> [!NOTE]
> Gli ActivityDesigner personalizzati possono essere utilizzati per le attività personalizzate e per le attività .NET predefinite.

## <a name="see-also"></a>Vedere anche

- [Usare il Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Flussi di lavoro di progettazione (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)