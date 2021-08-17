---
title: 'Excel: Introduzione alla programmazione delle personalizzazioni a livello di documento'
description: Informazioni su cosa è necessario sapere per iniziare a creare personalizzazioni a livello di documento Microsoft Office Excel usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fc808765dc4691ea35c8d3fdf91f4af04b4e8efd9221e8b02a98449ab63751d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424333"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel
  Se si è appena iniziato a creare personalizzazioni a livello di documento Microsoft Office Excel usando Visual Studio, ecco cosa è necessario sapere.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Informazioni sul funzionamento delle personalizzazioni a livello Excel documento
 Una personalizzazione a livello di documento Excel basata su una singola cartella di lavoro. Per iniziare a usare la personalizzazione, l'utente finale apre la cartella di lavoro o crea la cartella di lavoro da un Excel modello. Gli eventi nella cartella di lavoro, ad esempio la digitazione nelle celle o la selezione di pulsanti e voci di menu, possono chiamare metodi di gestione degli eventi nell'assembly. Quando la cartella di lavoro viene chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Excel, solo nel documento che le contiene.

 Per altre informazioni, vedere [Architettura delle personalizzazioni a livello di documento.](../vsto/architecture-of-document-level-customizations.md)

## <a name="create-document-level-projects-for-excel"></a>Creare progetti a livello di documento per Excel
 Per creare una personalizzazione a livello di documento per Excel, usare il modello di progetto Cartella di lavoro Excel o Modello Excel nella finestra di dialogo Nuovo **Project.** Questi modelli includono riferimenti dell'assembly e file di progetto necessari.

 Per altre informazioni su come creare un progetto a livello di documento per Excel, vedere [Procedura:](../vsto/how-to-create-office-projects-in-visual-studio.md)Creare Office progetti in Visual Studio . Per altre informazioni sui modelli di progetto, vedere panoramica Office [dei modelli di progetto.](../vsto/office-project-templates-overview.md)

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmare Excel cartelle di lavoro usando elementi host e controlli host
 *Gli elementi* host e *i controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento create usando Visual Studio.

 Gli elementi host forniscono un punto di ingresso per il codice e possono anche fungere da contenitori per i controlli host e Windows Form. Nei progetti a livello di documento Excel, questi elementi host sono rappresentati dalle `ThisWorkbook` classi , , e `Sheet1` `Sheet2` `Sheet3` .

 I controlli host sono basati su oggetti Excel nativi, ad esempio oggetti elenco e intervalli. I controlli host offrono funzionalità simili agli oggetti Excel nativi, ma hanno anche nuovi eventi, supporto della finestra di progettazione e data binding funzionalità. Vengono visualizzati come oggetti di prima classe nel codice del progetto e in IntelliSense, semplificando così il riferimento a oggetti specifici direttamente nel codice senza dover esplorare il modello Excel a oggetti.

 Per altre informazioni, vedere i seguenti argomenti:

- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)

- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)

- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Personalizzare l'interfaccia utente di Excel
 La maggior Microsoft Office modifica l'interfaccia utente dell'applicazione Office per consentire agli utenti di interagire con la soluzione. Esistono molti modi in cui è possibile modificare l'interfaccia utente di Excel usando una personalizzazione a livello di documento. È ad esempio possibile aggiungere controlli alla barra multifunzione oppure visualizzare un riquadro azioni. Per altre informazioni, vedere Personalizzare [l'Office dell'interfaccia utente.](../vsto/office-ui-customization.md)

 È anche possibile aprire la cartella di lavoro associata al progetto direttamente in Visual Studio. Quando la cartella di lavoro è aperta in Visual Studio, è possibile modificare la cartella di lavoro usando l Excel'interfaccia utente. È anche possibile usare la cartella di lavoro come area di progettazione, che consente di trascinare i controlli nei fogli di lavoro. Per altre informazioni, vedere [Office progetti nell'ambiente Visual Studio .](../vsto/office-projects-in-the-visual-studio-environment.md)

## <a name="use-data-binding"></a>Usare data binding
 I controlli host sono anche nell'elenco dei controlli che è possibile trascinare dalla **finestra Origini** dati . L'aggiunta di controlli host in questo modo li associa automaticamente all'origine dati impostata tramite la finestra . Senza scrivere codice, è possibile visualizzare i dati di database, servizi Web e oggetti business. Per altre informazioni, vedere [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare una personalizzazione a livello di documento per Excel, vedere Procedura [dettagliata:](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)Creare la prima personalizzazione a livello di documento per Excel . Questa procedura dettagliata illustra gli strumenti Office di sviluppo in Visual Studio e il modello di programmazione per Excel personalizzazioni a livello di documento.

 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti Excel, vedere [Attività comuni nella](../vsto/common-tasks-in-office-programming.md)programmazione Office .

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Excel soluzioni](../vsto/excel-solutions.md)
- [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
