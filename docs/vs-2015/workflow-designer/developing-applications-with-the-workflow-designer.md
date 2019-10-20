---
title: Sviluppo di applicazioni con il Progettazione flussi di lavoro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656820"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Sviluppo di applicazioni con Progettazione flussi di lavoro
[!INCLUDE[wfd1](../includes/wfd1-md.md)] consiste in un debugger e una finestra di progettazione visiva per il debug e la costruzione grafica di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] nella versione [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] ospitata nell'ambiente di sviluppo di [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Consente di creare un'applicazione di flussi di lavoro compositi, una libreria attività o un servizio [!INCLUDE[indigo1](../includes/indigo1-md.md)] tramite l'uso di modelli e ActivityDesigner. [!INCLUDE[crabout](../includes/crabout-md.md)] i flussi di lavoro, [vedere &#91;Windows Workflow Foundation .NET Framework&#93;4](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Di seguito sono indicate diverse nuove funzionalità di progettazione che fanno la distinzione tra questa nuova versione di [!INCLUDE[wfd2](../includes/wfd2-md.md)] e le versioni precedenti di [!INCLUDE[wfd2](../includes/wfd2-md.md)]:

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] è basato su [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Questo aspetto migliora l'esperienza con gli ActivityDesigner e le prestazioni nei casi di flussi di lavoro complessi e di grandi dimensioni.

- Le attività personalizzate sono ora progettate con [!INCLUDE[avalon2](../includes/avalon2-md.md)]. L'utilizzo del modello di programmazione e di XAML per la creazione di ActivityDesigner è stato semplificato.

- È stata implementata un'attività Flowchart, in modo da visualizzare il flusso di programma usando lo stile comune di modellazione del diagramma di flusso.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] presenta una nuova finestra di progettazione variabili che consente di dichiarare e assegnare un ambito alle variabili nei flussi di lavoro, associandole alle attività.

- In [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] fornisce funzionalità IntelliSense complete quando vengono create espressioni di Visual Basic nei flussi di lavoro di [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

- L'esperienza di debug si estende ora a XAML, per consentire l'impostazione dei punti di interruzione nella definizione del flusso di lavoro XAML e di eseguire istruzioni nel codice XAML in fase di esecuzione, diventando in questo modo simile all'esperienza del codice gestito.

- La riallocazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)] esternamente a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene semplificata in modo significativo rispetto alle versioni precedenti dal momento che ora è sufficiente specificare solo alcune righe di codice.

- La nuova attività <xref:System.Activities.Statements.Flowchart> e il relativo [diagramma](../workflow-designer/flowchart-activity-designer.md) di flusso consentono di visualizzare il flusso del programma usando lo stile di modellazione del diagramma di flusso noto.

- Le attività di messaggistica sono state migliorate per consentire la scrittura di servizi [!INCLUDE[indigo1](../includes/indigo1-md.md)] completamente dichiarativi (senza codice).

- **Aggiungi riferimento al servizio...** la funzionalità consente di generare automaticamente le attività che accedono ai servizi Web.

## <a name="in-this-section"></a>Contenuto della sezione
 [Uso della progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md) Viene illustrato come creare nuove attività e progetti del flusso di lavoro utilizzando le finestre di progettazione predefinite e come utilizzare altri strumenti forniti dalla finestra di progettazione per gestire argomenti, variabili, espressioni, importazioni e navigazione di navigazione.

 [Utilizzo dell'](../workflow-designer/using-the-activity-designers.md) ActivityDesigner Vengono descritte le categorie di attività e modelli e le relative finestre di progettazione fornite dal sistema.

 [Debug dei flussi di lavoro con il progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Viene descritto come eseguire le tradizionali procedure di debug, nonché come eseguire il debug di XAML ed espressioni.

 [Guida dell'interfaccia utente di progettazione flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md) Contiene argomenti della Guida sensibili al contesto per le finestre di dialogo fornite da [!INCLUDE[wfd1](../includes/wfd1-md.md)], nonché indicazioni sulle funzionalità della shell della finestra di progettazione, tasti di scelta rapida e messaggi di errore.

 [Sviluppo di applicazioni flusso di lavoro destinate a .net 3,0 o .net 3,5 Framework](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Contiene informazioni aggiuntive sull'utilizzo della finestra di progettazione legacy destinata al [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o al [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [ &#91;Esempi&#93; di riallocazione WF di progettazione](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) In questo esempio viene illustrato come creare il layout WPF per contenere la finestra di progettazione.

 ActivityDesigner [personalizzati](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Questa sezione contiene esempi di attività che usano finestre di progettazione personalizzate per la visualizzazione in Progettazione flussi di lavoro.