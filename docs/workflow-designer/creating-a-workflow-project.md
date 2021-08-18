---
title: Creare un progetto Workflow Foundation
description: Informazioni su come creare librerie e applicazioni con i modelli di progetto disponibili in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: conceptual
helpviewer_keywords:
- Workflow Designer, creating a workflow project
- creating a workflow project
ms.assetid: 235a125e-ebe7-4a98-bf77-86c8558728fb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: adb28a3ffd44e1cfcd744ab603d9c7e8555cafc3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155226"
---
# <a name="workflow-project-templates"></a>Modelli di progetto del flusso di lavoro

È possibile creare flussi di lavoro, Windows servizi flusso di lavoro di Communication Foundation (WCF), attività personalizzate e ActivityDesigner personalizzati usando Visual Studio di progetto. Questo articolo descrive come creare librerie e applicazioni con i modelli di progetto disponibili in Visual Studio.

## <a name="create-a-workflow-project"></a>Creare un progetto flusso di lavoro

Visual Studio fornisce quattro diversi modelli di progetto flusso di lavoro:

- App console del flusso di lavoro

- App del servizio flusso di lavoro WCF

- Libreria di attività

- Libreria di ActivityDesigner

Per accedere a questi modelli, installare prima il **componente Windows Workflow Foundation** di Visual Studio. Per istruzioni dettagliate, vedere [Installare Windows Workflow Foundation.](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)

1. Dopo aver installato il componente **Windows Workflow Foundation,** selezionare **File**  >    >  **nuovo Project**.

1. Cercare e selezionare un modello di progetto flusso di lavoro, ad esempio il modello **Applicazione console** flusso di lavoro.

1. Continuare per creare il progetto.

   > [!NOTE]
   > Se si vuole aggiungere un nuovo progetto a una soluzione esistente, aprirla in Visual Studio, fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere Aggiungi nuovo  >  **Project**.

## <a name="workflow-console-app"></a>App console del flusso di lavoro

Se si sceglie il modello **Applicazione console** flusso di lavoro, Visual Studio una definizione del flusso di lavoro in XAML. Verrà Progettazione flussi di lavoro visualizzato il canvas per il flusso di lavoro creato. Per comporre un flusso di lavoro, trascinare attività o altri elementi del flusso di lavoro dalla **Casella degli** strumenti all'area di progettazione.

## <a name="wcf-workflow-service-app"></a>App del servizio flusso di lavoro WCF

Se si sceglie il modello Applicazione servizio flusso di lavoro **WCF,** Visual Studio una definizione del servizio come XAML. Il Progettazione flussi di lavoro si apre alla visualizzazione progettazione con <xref:System.Activities.Statements.Sequence> un'attività che contiene un set di attività e <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> .

## <a name="activity-library"></a>Libreria di attività

Se si sceglie il **modello Libreria di** attività, Visual Studio una definizione di attività in XAML. Progettazione flussi di lavoro apre e visualizza l'area di disegno per l'attività personalizzata. Trascinare un'attività **dalla Casella** degli strumenti all'area di progettazione per includerla nell'attività personalizzata.

> [!NOTE]
> È consentita una sola attività figlio nel corpo dell'attività personalizzata. Tale attività figlio può tuttavia essere un'attività composita, ad esempio <xref:System.Activities.Statements.Sequence> un'attività o <xref:System.Activities.Statements.Flowchart> un'attività.

## <a name="activity-designer-library"></a>Libreria di ActivityDesigner

Se si sceglie il **modello Libreria di ActivityDesigner,** Visual Studio crea una definizione di ActivityDesigner in XAML e un file di implementazione code-behind. Verrà Progettazione flussi di lavoro visualizzato l'area di disegno per l'ActivityDesigner. Trascinare Windows Presentation Foundation (WPF) dalla **Casella degli** strumenti all'area di progettazione per usarli nell'ActivityDesigner personalizzato.

Per un esempio di come implementare un ActivityDesigner personalizzato, vedere [Procedura: Creare un ActivityDesigner personalizzato.](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer)

> [!NOTE]
> Gli ActivityDesigner personalizzati possono essere usati per le attività personalizzate e per le attività .NET predefinite.

## <a name="see-also"></a>Vedi anche

- [Utilizzare Progettazione flussi di lavoro](developing-applications-with-the-workflow-designer.md)
- [Progettare flussi di lavoro (.NET Framework)](/dotnet/framework/windows-workflow-foundation/designing-workflows)
