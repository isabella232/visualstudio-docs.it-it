---
title: Sviluppo di applicazioni con Progettazione flussi di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Sviluppo di applicazioni con Progettazione flussi di lavoro

La finestra di progettazione del flusso di lavoro di Windows è una finestra di progettazione visiva e del debugger per la costruzione grafica e il debug delle applicazioni di Windows Workflow Foundation (WF) in .NET Framework 4 è ospitato nell'ambiente di sviluppo di Visual Studio 2010. Consente di comporre un applicazione flusso di lavoro compositi, libreria di attività o servizio di Windows Communication Foundation (WCF) tramite l'uso di ActivityDesigner e modelli. Per ulteriori informazioni sui flussi di lavoro, vedere il [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Di seguito sono diverse nuove caratteristiche di progettazione che consente di impostare questa nuova versione della finestra di progettazione del flusso di lavoro oltre a versioni precedenti della finestra di progettazione del flusso di lavoro:

-   La finestra di progettazione del flusso di lavoro viene creata mediante Windows Presentation Foundation (WPF). Questo aspetto migliora l'esperienza con gli ActivityDesigner e le prestazioni nei casi di flussi di lavoro complessi e di grandi dimensioni.

-   Le attività personalizzate sono ora progettate con [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)]. L'utilizzo del modello di programmazione e di XAML per la creazione di ActivityDesigner è stato semplificato.

-   È stata implementata un'attività Flowchart, in modo da visualizzare il flusso di programma usando lo stile comune di modellazione del diagramma di flusso.

-   La finestra di progettazione del flusso di lavoro dispone di una nuova finestra di progettazione variabile che consente di dichiarare e assegnare un ambito variabili nei flussi di lavoro, associandole alle attività.

-   In Visual Studio 2010, la finestra di progettazione del flusso di lavoro fornisce funzionalità IntelliSense complete quando si creano le espressioni Visual Basic nei flussi di lavoro .NET Framework 4.

-   L'esperienza di debug si estende ora a XAML, per consentire l'impostazione dei punti di interruzione nella definizione del flusso di lavoro XAML e di eseguire istruzioni nel codice XAML in fase di esecuzione, diventando in questo modo simile all'esperienza del codice gestito.

-   Riallocazione della finestra di progettazione del flusso di lavoro all'esterno di Visual Studio sia notevolmente semplificato rispetto alle versioni precedenti, ora che richiedono solo poche righe di codice.

-   Il nuovo <xref:System.Activities.Statements.Flowchart> attività e il relativo [diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) consentono di visualizzare il flusso di programma utilizzando il diagramma di flusso stile di modellazione.

-   Sono state migliorate le attività di messaggistica, consentendo di scrivere completamente dichiarativi (senza codice) Servizi Windows Communication Foundation (WCF).

-   Il **Aggiungi riferimento al servizio...**  funzionalità consente di generare automaticamente le attività che accedere ai servizi Web.