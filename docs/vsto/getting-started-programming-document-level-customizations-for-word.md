---
title: Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5bed5c08e15861840a34960d186b408fb86085d
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2018
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
  Se per iniziare a creare personalizzazioni a livello di documento per Microsoft Office Word usando Visual Studio, ecco cosa è necessario conoscere.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Comprendere le personalizzazioni a livello di documento per Word  
 Ogni personalizzazione Word creata si basa su un singolo documento. Per iniziare a utilizzare la personalizzazione, l'utente finale apre un documento o crea il documento da un modello di Word. Gli eventi nel documento, ad esempio spostare il cursore all'interno di aree specifiche o facendo clic sui pulsanti e voci di menu, possono chiamare i metodi di gestione degli eventi nell'assembly. Quando il documento è chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Word.  
  
 Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento di](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Creare i progetti a livello di documento per Word  
 Per creare una personalizzazione a livello di documento per Word, usare il modello di progetto documento di Word o modello di Word nel **nuovo progetto** la finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari.  
  
 Per ulteriori informazioni su come creare un progetto a livello di documento per Word, vedere [procedura: progetti di Office Create in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [panoramica dei modelli di progetto Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Documenti di Word programma tramite i controlli host di elementi host  
 *Elementi host* e *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento.  
  
 Gli elementi host forniscono un punto di ingresso per il codice e può anche fungono da contenitori per i controlli host e controlli Windows Form. Nei progetti a livello di documento per Word, l'elemento host è rappresentato dalla `ThisDocument` classe.  
  
 Controlli host sono basati sugli oggetti nativi di Word, ad esempio i controlli del contenuto, i segnalibri e nodi XML. Controlli host offrono funzionalità simili per gli oggetti nativi di Word, ma dispongono anche di nuovi eventi, il supporto della finestra di progettazione e funzionalità di associazione dati. Vengono visualizzate come oggetti di prima classe nel codice del progetto in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover passare il modello a oggetti.  
  
 Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Elementi host e Cenni preliminari sui controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Personalizzare l'interfaccia utente di Word  
 La maggior parte delle soluzioni di Microsoft Office modificare l'interfaccia utente (UI) dell'applicazione di Office allo scopo di consentire agli utenti di interagire con la soluzione. Esistono molti modi in cui è possibile modificare l'interfaccia utente di Word usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione ed è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).  
  
 È anche possibile aprire il documento associato direttamente al progetto in Visual Studio. Quando il documento viene aperto in Visual Studio, è possibile modificare il documento tramite l'interfaccia utente di Word. È anche possibile utilizzare il documento come area di progettazione, che consente di trascinare i controlli su di esso. Per altre informazioni, vedere [progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Associare i controlli ai dati  
 I controlli contenuto e <xref:Microsoft.Office.Tools.Word.Bookmark> controllo sono presenti nell'elenco di controlli che è possibile trascinare il **origini dati** finestra. Aggiunta di controlli del contenuto e segnalibri in questo modo automaticamente li associa l'origine dati impostate utilizzando la finestra. Senza scrivere alcun codice, è possibile visualizzare i dati dal database, servizi e oggetti business. Per altre informazioni, vedere [associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per informazioni su come creare una personalizzazione a livello di documento per Word, vedere [procedura dettagliata: creazione di una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Questa procedura dettagliata illustra gli strumenti di sviluppo per Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Word.  
  
 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Word, vedere [attività comuni nella programmazione con Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Procedura dettagliata: Creazione di una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  