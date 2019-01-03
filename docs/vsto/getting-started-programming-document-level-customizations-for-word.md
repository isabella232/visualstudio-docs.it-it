---
title: Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 651208958b40ff92804b9989234f8c3822ec83d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904799"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
  Se sta iniziando la creazione di personalizzazioni a livello di documento per Microsoft Office Word usando Visual Studio, ecco cosa occorre sapere.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Comprendere personalizzazioni a livello di documento per Word  
 Ogni personalizzazione Word creata si basa su un singolo documento. Per iniziare a usare la personalizzazione, l'utente finale apre il documento o crea il documento da un modello di Word. Gli eventi nel documento, ad esempio spostare il cursore in aree specifiche o facendo clic su pulsanti e le voci di menu, è possono chiamare i metodi di gestione degli eventi nell'assembly. Quando il documento è chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Word.  
  
 Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Creare i progetti a livello di documento per Word  
 Per creare una personalizzazione a livello di documento per Word, usare il modello di progetto documento di Word o modello di Word nel **nuovo progetto** nella finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari.  
  
 Per altre informazioni su come creare un progetto a livello di documento per Word, vedere [come: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per altre informazioni sui modelli di progetto, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Documenti di Word programma tramite i controlli host di elementi host  
 *Elementi host* e *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento.  
  
 Elementi host forniscono un punto di ingresso per il codice e si può anche agire come contenitori per i controlli host e controlli Windows Form. Nei progetti a livello di documento per Word, l'elemento host è rappresentato dal `ThisDocument` classe.  
  
 Controlli host si basano sugli oggetti di Word nativi, ad esempio i controlli contenuto, segnalibri e i nodi XML. Controlli host forniscono funzionalità simili per gli oggetti nativi di Word, ma dispongono anche di nuovi eventi, il supporto della finestra di progettazione e funzionalità di associazione dati. Vengono visualizzati come oggetti di prima classe nel codice del progetto e in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza la necessità di passare il modello a oggetti Word.  
  
 Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Personalizzare l'interfaccia utente di Word  
 La maggior parte delle soluzioni di Microsoft Office modificare l'interfaccia utente (UI) dell'applicazione di Office allo scopo di consentire agli utenti di interagire con la soluzione. Esistono diversi modi in cui è possibile modificare l'interfaccia utente di Word usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione ed è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).  
  
 È anche possibile aprire il documento associata direttamente al progetto in Visual Studio. Quando il documento è aperto in Visual Studio, è possibile modificare il documento usando l'interfaccia utente di Word. È anche possibile utilizzare il documento come un'area di progettazione, che consente di trascinare i controlli su di esso. Per altre informazioni, vedere [progetti di Office in ambiente di Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Associare controlli ai dati  
 I controlli contenuto e il <xref:Microsoft.Office.Tools.Word.Bookmark> controllo incluse nell'elenco di controlli che è possibile trascinare dal **Zdroje dat** finestra. Aggiunta di controlli del contenuto e inserisce un segnalibro in questo modo automaticamente li associa all'origine dati impostata utilizzando la finestra. Senza scrivere alcun codice, è possibile visualizzare i dati dal database, servizi e oggetti business. Per altre informazioni, vedere [associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per informazioni su come creare una personalizzazione a livello di documento per Word, vedere [procedura dettagliata: Creare una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Questa procedura dettagliata presenta gli strumenti di sviluppo per Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Word.  
  
 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Word, vedere [attività comuni nella programmazione Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Procedura dettagliata: Creare una personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
