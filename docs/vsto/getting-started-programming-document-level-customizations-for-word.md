---
title: Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
description: Informazioni su cosa è necessario sapere per iniziare a creare personalizzazioni a livello di documento Microsoft Office Word usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9142781a7e06e2cf1f2546324551be7b5dc436ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026434"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
  Se si sta appena iniziare a creare personalizzazioni a livello di documento per Microsoft Office Word usando Visual Studio, ecco cosa è necessario sapere.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Informazioni sul funzionamento delle personalizzazioni a livello di documento per Word
 Ogni personalizzazione di Word creata si basa su un singolo documento. Per iniziare a usare la personalizzazione, l'utente finale apre il documento o crea il documento da un modello di Word. Gli eventi nel documento, ad esempio lo spostamento del cursore in aree specifiche o la selezione di pulsanti e voci di menu, possono chiamare metodi di gestione degli eventi nell'assembly. Quando il documento viene chiuso, le funzionalità fornite dalla personalizzazione non sono più disponibili in Word.

 Per altre informazioni, vedere [Architettura delle personalizzazioni a livello di documento.](../vsto/architecture-of-document-level-customizations.md)

## <a name="create-document-level-projects-for-word"></a>Creare progetti a livello di documento per Word
 Per creare una personalizzazione a livello di documento per Word, usare il modello di progetto Documento di Word o Modello di Word nella finestra di **dialogo Nuovo** Project documento. Questi modelli includono riferimenti dell'assembly e file di progetto necessari.

 Per altre informazioni su come creare un progetto a livello di documento per Word, vedere [Procedura:](../vsto/how-to-create-office-projects-in-visual-studio.md)Creare Office progetti in Visual Studio . Per altre informazioni sui modelli di progetto, vedere panoramica Office [dei modelli di progetto.](../vsto/office-project-templates-overview.md)

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programmare documenti di Word usando i controlli host degli elementi host
 *Gli elementi* host e *i controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento.

 Gli elementi host forniscono un punto di ingresso per il codice e possono anche fungere da contenitori per i controlli host e Windows Form. Nei progetti a livello di documento per Word, l'elemento host è rappresentato dalla `ThisDocument` classe .

 I controlli host sono basati su oggetti nativi di Word, ad esempio controlli contenuto, segnalibri e nodi XML. I controlli host offrono funzionalità simili agli oggetti nativi di Word, ma hanno anche nuovi eventi, supporto della finestra di progettazione e funzionalità di data binding. Vengono visualizzati come oggetti di prima classe nel codice del progetto e in IntelliSense, semplificando così il riferimento a oggetti specifici direttamente nel codice senza dover esplorare il modello a oggetti di Word.

 Per altre informazioni, vedere i seguenti argomenti:

- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)

- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)

- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Personalizzare l'interfaccia utente di Word
 La maggior Microsoft Office soluzioni modificano l'interfaccia utente dell'applicazione Office per consentire agli utenti di interagire con la soluzione. Esistono molti modi in cui è possibile modificare l'interfaccia utente di Word usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione ed è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere Personalizzare [l'Office dell'interfaccia utente.](../vsto/office-ui-customization.md)

 È anche possibile aprire il documento associato al progetto direttamente in Visual Studio. Quando il documento è aperto in Visual Studio, è possibile modificare il documento usando l'interfaccia utente di Word. È anche possibile usare il documento come area di progettazione, che consente di trascinare i controlli su di esso. Per altre informazioni, vedere [Office progetti nell'ambiente Visual Studio .](../vsto/office-projects-in-the-visual-studio-environment.md)

## <a name="bind-controls-to-data"></a>Associare i controlli ai dati
 I controlli contenuto e il controllo sono nell'elenco di controlli che <xref:Microsoft.Office.Tools.Word.Bookmark> è possibile trascinare dalla **finestra Origini** dati . L'aggiunta di controlli contenuto e segnalibri in questo modo li associa automaticamente all'origine dati impostata tramite la finestra . Senza scrivere codice, è possibile visualizzare i dati di database, servizi e oggetti business. Per altre informazioni, vedere [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare una personalizzazione a livello di documento per Word, vedere Procedura dettagliata: Creare la prima personalizzazione a livello [di documento per Word.](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md) Questa procedura dettagliata illustra gli strumenti di Office di sviluppo in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Word.

 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti word, vedere Attività comuni nella programmazione [Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Soluzioni Word](../vsto/word-solutions.md)
- [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
