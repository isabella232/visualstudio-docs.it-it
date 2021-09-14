---
title: soluzioni Excel
description: Informazioni su come usare i modelli di progetto per automatizzare Excel, estendere Excel funzionalità e personalizzare Excel'interfaccia utente
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 8bd3ab0ac5705a5af994ef51e1edde9d250124e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634084"
---
# <a name="excel-solutions"></a>soluzioni Excel
  Visual Studio fornisce modelli di progetto che è possibile usare per creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel. È possibile usare queste soluzioni per automatizzare Excel, estenderne le funzionalità e personalizzarne l'interfaccia utente. Per altre informazioni sulle differenze tra le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO, vedere panoramica dello sviluppo di Office soluzioni &#40;VSTO&#41;[. ](../vsto/office-solutions-development-overview-vsto.md)

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Questo argomento contiene informazioni sui seguenti aspetti:

- [Automatizzare Excel](#automating).

- [Sviluppare personalizzazioni a livello di documento per Excel](#doclevel).

- [Sviluppare VSTO componenti aggiuntivi per Excel](#applevel).

- [Personalizzare l'interfaccia utente di Excel](#UI).

## <a name="automate-excel"></a><a name="automating"></a>Automatizzare Excel
 Il modello a oggetti di Excel espone diversi tipi che è possibile usare per automatizzare Excel. Ad esempio, è possibile creare grafici, formattare fogli di lavoro e impostare i valori degli intervalli e delle celle a livello di codice. Per altre informazioni, vedere panoramica [Excel modello a oggetti](../vsto/excel-object-model-overview.md).

 Quando si sviluppano soluzioni Excel in Visual Studio, si possono anche usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono alcuni oggetti di uso comune nel modello a oggetti di Excel, ad esempio gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> e <xref:Microsoft.Office.Interop.Excel.Range> . Gli oggetti estesi si comportano come gli oggetti di Excel sui quali si basano, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti. Per altre informazioni, vedere [Automatizzare Excel usando oggetti estesi.](../vsto/automating-excel-by-using-extended-objects.md)

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a>Sviluppare personalizzazioni a livello di documento per Excel
 Una personalizzazione a livello di documento per Microsoft Office Excel è costituita da un assembly associato a una cartella di lavoro specifica. L'assembly in genere estende la cartella di lavoro personalizzando l'interfaccia utente e automatizzando Excel. Diversamente da un componente aggiuntivo VSTO a livello di applicazione, associato a Excel stesso, la funzionalità che si implementa in una personalizzazione è disponibile solo quando la cartella di lavoro associata è aperta in Excel.

 Per creare un progetto di personalizzazione a livello di documento per Excel, usare la cartella di lavoro di Excel o i modelli di progetto Excel nella finestra di **dialogo Nuovo Project** di Visual Studio. Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Per altre informazioni sul funzionamento delle personalizzazioni a livello di documento, vedere [Architettura delle personalizzazioni a livello di documento.](../vsto/architecture-of-document-level-customizations.md)

### <a name="excel-customization-programming-model"></a>Excel di programmazione della personalizzazione
 Quando si crea un progetto a livello di documento per Excel, in Visual Studio vengono generate diverse classi che costituiscono il fondamento della soluzione: `ThisWorkbook`, `Sheet1`, `Sheet2`e `Sheet3`. Queste classi rappresentano la cartella di lavoro e fogli di lavoro associati alla soluzione e forniscono un punto di partenza per la scrittura del codice.

 Per altre informazioni su queste classi generate e su altre funzionalità che è possibile usare in un progetto a livello di documento, vedere [Programmare personalizzazioni](../vsto/programming-document-level-customizations.md)a livello di documento.

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a>Sviluppare VSTO componenti aggiuntivi per Excel
 Un componente aggiuntivo VSTO per Microsoft Office Excel è costituito da un assembly caricato da Excel. L'assembly in genere estende Excel personalizzando l'interfaccia utente e automatizzando Excel. A differenza di una personalizzazione a livello di documento, associata a una cartella di lavoro specifica, la funzionalità implementata in un componente aggiuntivo VSTO non è limitata ad alcuna singola cartella di lavoro.

 Per creare un progetto di componente aggiuntivo VSTO per Excel, usare la cartella di lavoro di Excel o i modelli di progetto modello di Excel nella finestra di dialogo Nuovo **Project** di Visual Studio. Per altre informazioni, [vedere Procedura: Creare Office progetti in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Per informazioni generali sul funzionamento dei componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Excel Modello di programmazione dei componenti aggiuntivi
 Quando si crea un progetto di componente aggiuntivo VSTO per Excel, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone anche il modello a oggetti di Excel nel componente aggiuntivo VSTO.

 Per altre informazioni sulla classe e su altre funzionalità Visual Studio che è possibile usare in un componente aggiuntivo VSTO, vedere Componenti aggiuntivi VSTO `ThisAddIn` [programma.](../vsto/programming-vsto-add-ins.md)

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a>Personalizzare l'interfaccia utente di Excel
 Sono disponibili diverse modalità per personalizzare l'interfaccia utente di Excel. Alcune opzioni sono disponibili per tutti i tipi di progetto e altre opzioni sono disponibili solo per i componenti aggiuntivi VSTO o le personalizzazioni a livello di documento.

### <a name="options-for-all-project-types"></a>Opzioni per tutti i tipi di progetto
 La tabella seguente elenca le opzioni di personalizzazione disponibili per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Personalizzare la barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Aggiungere controlli Windows Form o controlli estesi di Excel a un foglio di lavoro della cartella di lavoro personalizzata per una personalizzazione a livello di documento, o in qualsiasi cartella di lavoro aperta per un componente aggiuntivo VSTO.|[Procedura: Aggiungere controlli Windows form personalizzati a Office documenti](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Procedura: Aggiungere controlli Chart ai fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Procedura: Aggiungere controlli ListObject ai fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Procedura: Aggiungere controlli NamedRange ai fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Opzioni per le personalizzazioni a livello di documento
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per le personalizzazioni a livello di documento.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Aggiunta di un riquadro delle azioni alla cartella di lavoro.|[Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)<br /><br /> [Procedura: Aggiungere un riquadro azioni a documenti di Word o Excel cartelle di lavoro](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Aggiungere a un foglio di lavoro controlli di intervallo esteso mappati ai nodi XML.|[Procedura: Aggiungere controlli XMLMappedRange ai fogli di lavoro](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Opzioni per i componenti aggiuntivi VSTO
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per i componenti aggiuntivi VSTO.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md) | Fornisce una panoramica dei tipi principali forniti dal modello a oggetti di Excel. |
| [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md) | Fornisce informazioni sugli oggetti estesi (forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) che è possibile usare nelle soluzioni Excel. |
| [Globalizzazione e localizzazione di Excel soluzioni](../vsto/globalization-and-localization-of-excel-solutions.md) | Contiene considerazioni speciali per le soluzioni Excel eseguite in computer che hanno impostazioni di Windows non in inglese. |
| [Windows Panoramica dei controlli form Office documenti](../vsto/windows-forms-controls-on-office-documents-overview.md) | Descrive come è possibile aggiungere controlli Windows Form ai fogli di lavoro di Excel. |
| [Procedura dettagliata: Creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Illustra come creare una personalizzazione di base a livello di documento per Excel. |
| [Procedura dettagliata: Creare il primo VSTO per l'Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Mostra come creare un componente aggiuntivo VSTO di base per Excel. |
| [Procedura dettagliata: Aggiungere controlli a un foglio di lavoro in fase di VSTO progetto di componente aggiuntivo](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Illustra come aggiungere un pulsante di Windows Form, <xref:Microsoft.Office.Tools.Excel.NamedRange>e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di esecuzione con un componente aggiuntivo VSTO. |
| [Informazioni sulla creazione condivisa e i componenti aggiuntivi](./understanding-coauthoring-and-addins.md) | Descrive le modifiche che potrebbe essere necessario apportare alle soluzioni per supportare la creazione condivisa. |
| [Excel 2010 in Office sviluppo](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Fornisce collegamenti ad articoli e documentazione di riferimento sullo sviluppo di soluzioni Excel. Gli articoli non sono specifici per lo sviluppo di Office usando Visual Studio. |
