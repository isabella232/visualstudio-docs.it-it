---
title: Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
description: Informazioni su cosa è necessario sapere per iniziare a creare personalizzazioni a livello di documento per Microsoft Office Word con Visual Studio.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9420ab02b5f402dd39e5ca1713b911a10932dfb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845180"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Word
  Se si sta iniziando a creare personalizzazioni a livello di documento per Microsoft Office Word con Visual Studio, ecco cosa è necessario conoscere.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Informazioni sulle personalizzazioni a livello di documento per Word Work
 Ogni personalizzazione di Word creata si basa su un singolo documento. Per iniziare a usare la personalizzazione, l'utente finale apre il documento o crea il documento da un modello di Word. Gli eventi del documento, ad esempio il passaggio del cursore in aree specifiche o la selezione di pulsanti e voci di menu, possono chiamare metodi di gestione degli eventi nell'assembly. Quando il documento viene chiuso, le funzionalità fornite dalla personalizzazione non sono più disponibili in Word.

 Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Creare progetti a livello di documento per Word
 Per creare una personalizzazione a livello di documento per Word, usare il modello di progetto documento di Word o modello di Word nella finestra di dialogo **nuovo progetto** . Questi modelli includono riferimenti dell'assembly e file di progetto necessari.

 Per altre informazioni su come creare un progetto a livello di documento per Word, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programmare documenti Word usando gli elementi host controlli host
 *Gli elementi host* e i *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento.

 Gli elementi host forniscono un punto di ingresso per il codice e possono fungere anche da contenitori per controlli host e controlli Windows Forms. Nei progetti a livello di documento per Word, l'elemento host è rappresentato dalla `ThisDocument` classe.

 I controlli host sono basati su oggetti nativi di Word, ad esempio controlli contenuto, segnalibri e nodi XML. I controlli host forniscono funzionalità simili agli oggetti nativi di Word, ma dispongono anche di nuovi eventi, supporto della finestra di progettazione e funzionalità di data binding. Vengono visualizzati come oggetti di prima classe nel codice del progetto e in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover esplorare il modello a oggetti di Word.

 Per altre informazioni, vedere i seguenti argomenti:

- [Programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)

- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)

- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Personalizzare l'interfaccia utente di Word
 La maggior parte delle soluzioni Microsoft Office modifica l'interfaccia utente dell'applicazione di Office in modo da consentire agli utenti di interagire con la soluzione. Esistono diversi modi in cui è possibile modificare l'interfaccia utente di Word usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione ed è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).

 È anche possibile aprire il documento associato al progetto direttamente in Visual Studio. Quando il documento è aperto in Visual Studio, è possibile modificarlo usando l'interfaccia utente di Word. È inoltre possibile utilizzare il documento come area di progettazione, che consente di trascinare i controlli su di esso. Per altre informazioni, vedere [progetti di Office nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Associare i controlli ai dati
 I controlli contenuto e il <xref:Microsoft.Office.Tools.Word.Bookmark> controllo si trovano nell'elenco dei controlli che è possibile trascinare dalla finestra **origini dati** . L'aggiunta di controlli contenuto e segnalibri in questo modo li associa automaticamente all'origine dati configurata tramite la finestra di. Senza scrivere codice, è possibile visualizzare i dati di database, servizi e oggetti business. Per altre informazioni, vedere [associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare una personalizzazione a livello di documento per Word, vedere [procedura dettagliata: creare la prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Questa procedura dettagliata presenta gli strumenti di sviluppo di Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Word.

 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Word, vedere [attività comuni nella programmazione di Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Soluzioni Word](../vsto/word-solutions.md)
- [Procedura dettagliata: creare la prima personalizzazione a livello di documento per Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
