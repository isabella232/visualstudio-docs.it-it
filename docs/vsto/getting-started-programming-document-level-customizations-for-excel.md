---
title: 'Excel: Introduzione alla programmazione delle personalizzazioni a livello di documento'
description: Informazioni su cosa è necessario sapere per iniziare a creare personalizzazioni a livello di documento per Microsoft Office Excel usando Visual Studio.
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
ms.workload:
- office
ms.openlocfilehash: de5d7529e0bd8bc99eb4f375a31dab9ea9520234
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860724"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Introduzione alla programmazione delle personalizzazioni a livello di documento per Excel
  Se si sta iniziando a creare personalizzazioni a livello di documento per Microsoft Office Excel usando Visual Studio, ecco cosa è necessario conoscere.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Informazioni sul funzionamento delle personalizzazioni a livello di documento per Excel
 Una personalizzazione a livello di documento per Excel si basa su una singola cartella di lavoro. Per iniziare a utilizzare la personalizzazione, l'utente finale apre la cartella di lavoro o crea la cartella di lavoro da un modello di Excel. Gli eventi della cartella di lavoro, ad esempio la digitazione di celle o la selezione di pulsanti e voci di menu, possono chiamare metodi di gestione degli eventi nell'assembly. Quando la cartella di lavoro viene chiusa, le funzionalità fornite dalla personalizzazione non sono più disponibili in Excel, solo nel documento che li contiene.

 Per altre informazioni, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Creazione di progetti a livello di documento per Excel
 Per creare una personalizzazione a livello di documento per Excel, usare il modello di progetto cartella di lavoro di Excel o modello di Excel nella finestra di dialogo **nuovo progetto** . Questi modelli includono riferimenti dell'assembly e file di progetto necessari.

 Per altre informazioni su come creare un progetto a livello di documento per Excel, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per ulteriori informazioni sui modelli di progetto, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmare le cartelle di lavoro di Excel tramite elementi host e controlli host
 *Gli elementi* e i *controlli host* sono classi che forniscono il modello di programmazione per le personalizzazioni a livello di documento create tramite Visual Studio.

 Gli elementi host forniscono un punto di ingresso per il codice e possono fungere anche da contenitori per controlli host e controlli Windows Form. Nei progetti a livello di documento per Excel questi elementi host sono rappresentati dalle `ThisWorkbook` `Sheet1` classi,, `Sheet2` e `Sheet3` .

 I controlli host sono basati su oggetti nativi di Excel, ad esempio oggetti elenco e intervalli. I controlli host forniscono funzionalità simili agli oggetti nativi di Excel, ma dispongono anche di nuovi eventi, supporto della finestra di progettazione e funzionalità data binding. Vengono visualizzati come oggetti di prima classe nel codice del progetto e in IntelliSense, che rende più semplice fare riferimento a oggetti specifici direttamente nel codice senza dover esplorare il modello a oggetti di Excel.

 Per altre informazioni, vedere i seguenti argomenti:

- [Programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)

- [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)

- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Personalizzare l'interfaccia utente di Excel
 La maggior parte delle soluzioni Microsoft Office modifica l'interfaccia utente dell'applicazione di Office in modo da consentire agli utenti di interagire con la soluzione. Esistono diversi modi in cui è possibile modificare l'interfaccia utente di Excel usando una personalizzazione a livello di documento. Ad esempio, è possibile aggiungere controlli alla barra multifunzione oppure è possibile visualizzare un riquadro azioni. Per altre informazioni, vedere [personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).

 È anche possibile aprire la cartella di lavoro associata al progetto direttamente in Visual Studio. Quando la cartella di lavoro è aperta in Visual Studio, è possibile modificare la cartella di lavoro tramite l'interfaccia utente di Excel. È inoltre possibile utilizzare la cartella di lavoro come area di progettazione, che consente di trascinare i controlli sui fogli di lavoro. Per altre informazioni, vedere [progetti di Office nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Usa data binding
 I controlli host sono inclusi anche nell'elenco dei controlli che è possibile trascinare dalla finestra **origini dati** . L'aggiunta di controlli host in questo modo li associa automaticamente all'origine dati configurata mediante la finestra. Senza scrivere codice, è possibile visualizzare i dati di database, servizi Web e oggetti business. Per altre informazioni, vedere [associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare una personalizzazione a livello di documento per Excel, vedere [procedura dettagliata: creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Questa procedura dettagliata presenta gli strumenti di sviluppo di Office in Visual Studio e il modello di programmazione per le personalizzazioni a livello di documento di Excel.

 Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Excel, vedere [attività comuni nella programmazione di Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programma personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
- [Soluzioni Excel](../vsto/excel-solutions.md)
- [Procedura dettagliata: creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)
- [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
