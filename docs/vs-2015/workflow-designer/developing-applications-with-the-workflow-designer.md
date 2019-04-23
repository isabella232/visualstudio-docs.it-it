---
title: Sviluppo di applicazioni con Progettazione flussi di lavoro | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 71fdd358c03604b196b0a57a9667f40dfb92b049
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073969"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Sviluppo di applicazioni con Progettazione flussi di lavoro
[!INCLUDE[wfd1](../includes/wfd1-md.md)] consiste in un debugger e una finestra di progettazione visiva per il debug e la costruzione grafica di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] nella versione [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] ospitata nell'ambiente di sviluppo di [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Consente di creare un'applicazione di flussi di lavoro compositi, una libreria attività o un servizio [!INCLUDE[indigo1](../includes/indigo1-md.md)] tramite l'uso di modelli e ActivityDesigner. [!INCLUDE[crabout](../includes/crabout-md.md)] flussi di lavoro, vedere la [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 Di seguito sono indicate diverse nuove funzionalità di progettazione che fanno la distinzione tra questa nuova versione di [!INCLUDE[wfd2](../includes/wfd2-md.md)] e le versioni precedenti di [!INCLUDE[wfd2](../includes/wfd2-md.md)]:  
  
- [!INCLUDE[wfd2](../includes/wfd2-md.md)] è basato su [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Questo aspetto migliora l'esperienza con gli ActivityDesigner e le prestazioni nei casi di flussi di lavoro complessi e di grandi dimensioni.  
  
- Le attività personalizzate sono ora progettate con [!INCLUDE[avalon2](../includes/avalon2-md.md)]. L'utilizzo del modello di programmazione e di XAML per la creazione di ActivityDesigner è stato semplificato.  
  
- È stata implementata un'attività Flowchart, in modo da visualizzare il flusso di programma usando lo stile comune di modellazione del diagramma di flusso.  
  
- [!INCLUDE[wfd2](../includes/wfd2-md.md)] presenta una nuova finestra di progettazione variabili che consente di dichiarare e assegnare un ambito alle variabili nei flussi di lavoro, associandole alle attività.  
  
- In [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] fornisce funzionalità IntelliSense complete quando vengono create espressioni di Visual Basic nei flussi di lavoro di [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].  
  
- L'esperienza di debug si estende ora a XAML, per consentire l'impostazione dei punti di interruzione nella definizione del flusso di lavoro XAML e di eseguire istruzioni nel codice XAML in fase di esecuzione, diventando in questo modo simile all'esperienza del codice gestito.  
  
- La riallocazione di [!INCLUDE[wfd2](../includes/wfd2-md.md)] esternamente a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene semplificata in modo significativo rispetto alle versioni precedenti dal momento che ora è sufficiente specificare solo alcune righe di codice.  
  
- Il nuovo <xref:System.Activities.Statements.Flowchart> attività e la relativa [Flowchart](../workflow-designer/flowchart-activity-designer.md) consentono di visualizzare il flusso di programma utilizzando il diagramma di flusso stile di modellazione.  
  
- Le attività di messaggistica sono state migliorate per consentire la scrittura di servizi [!INCLUDE[indigo1](../includes/indigo1-md.md)] completamente dichiarativi (senza codice).  
  
- Il **Aggiungi riferimento al servizio...** la funzionalità consente di generare automaticamente le attività che accedere ai servizi Web.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Uso di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)  
 Viene illustrato come creare nuove attività e progetti flusso di lavoro usando le finestre di progettazione incorporate e come usare gli altri strumenti forniti dalla finestra di progettazione per gestire argomenti, variabili, espressioni, importazioni e navigazioni.  
  
 [Uso degli Activity Designer](../workflow-designer/using-the-activity-designers.md)  
 Vengono descritte le categorie di attività e modelli e le relative finestre di progettazione forniti dal sistema.  
  
 [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Viene illustrato come eseguire routine di debug tradizionali nonché il debug di espressioni e codice XAML.  
  
 [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md)  
 Contiene argomenti della Guida sensibili al contesto per finestre di dialogo fornite dalla [!INCLUDE[wfd1](../includes/wfd1-md.md)] nonché linee guida sulle funzionalità della shell della finestra di progettazione, le scelte rapide da tastiera e i messaggi di errore.  
  
 [Sviluppo di applicazioni flusso di lavoro destinate a Framework .NET 3.0 o Framework .NET 3.5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contiene il materiale sussidiario sull'utilizzo della finestra di progettazione legacy che viene destinata a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [Riallocazione della finestra di progettazione &#91;esempi di WF&#93;](http://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 In questo esempio viene illustrato come creare il layout WPF per contenere la finestra di progettazione.  
  
 [ActivityDesigner personalizzati](http://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075)  
 Contenuto della sezione sono contenuti esempi di attività in cui vengono usate finestre di progettazione personalizzate da visualizzare nella progettazione flussi di lavoro.