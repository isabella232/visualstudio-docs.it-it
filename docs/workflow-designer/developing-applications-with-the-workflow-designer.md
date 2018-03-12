---
title: Sviluppo di applicazioni con Progettazione flussi di lavoro | Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 75a6fb6eef1f5e8e174607ac141646ab237dd285
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Sviluppo di applicazioni con Progettazione flussi di lavoro

La finestra di progettazione del flusso di lavoro di Windows è una finestra di progettazione visiva e del debugger per la costruzione grafica e il debug di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] le applicazioni di [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] che è ospitato nel [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ambiente di sviluppo. Consente di creare un'applicazione di flussi di lavoro compositi, una libreria attività o un servizio [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] tramite l'uso di modelli e ActivityDesigner. Per ulteriori informazioni sui flussi di lavoro, vedere il [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Di seguito sono indicate diverse nuove caratteristiche di progettazione che fanno la distinzione tra questa nuova versione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] e le versioni precedenti di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] è basato su [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Questo aspetto migliora l'esperienza con gli ActivityDesigner e le prestazioni nei casi di flussi di lavoro complessi e di grandi dimensioni.

-   Le attività personalizzate sono ora progettate con [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)]. L'utilizzo del modello di programmazione e di XAML per la creazione di ActivityDesigner è stato semplificato.

-   È stata implementata un'attività Flowchart, in modo da visualizzare il flusso di programma usando lo stile comune di modellazione del diagramma di flusso.

-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] presenta una nuova finestra di progettazione variabili che consente di dichiarare e assegnare un ambito alle variabili nei flussi di lavoro, associandole alle attività.

-   In [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornisce funzionalità IntelliSense complete quando vengono create espressioni di Visual Basic nei flussi di lavoro di [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].

-   L'esperienza di debug si estende ora a XAML, per consentire l'impostazione dei punti di interruzione nella definizione del flusso di lavoro XAML e di eseguire istruzioni nel codice XAML in fase di esecuzione, diventando in questo modo simile all'esperienza del codice gestito.

-   La riallocazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] esternamente a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene semplificata in modo significativo rispetto alle versioni precedenti dal momento che ora è sufficiente specificare solo alcune righe di codice.

-   Il nuovo <xref:System.Activities.Statements.Flowchart> attività e il relativo [diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) consentono di visualizzare il flusso di programma utilizzando il diagramma di flusso stile di modellazione.

-   Le attività di messaggistica sono state migliorate per consentire la scrittura di servizi [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] completamente dichiarativi (senza codice).

-   Il **Aggiungi riferimento al servizio...**  funzionalità consente di generare automaticamente le attività che accedere ai servizi Web.