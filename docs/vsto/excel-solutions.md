---
title: soluzioni Excel
description: Informazioni su come usare i modelli di progetto per automatizzare Excel, estendere le funzionalità di Excel e personalizzare l'interfaccia utente di Excel
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
ms.workload:
- office
ms.openlocfilehash: 3833ff549b2cceb3f783afc43a4f71dacc00ecb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931279"
---
# <a name="excel-solutions"></a>soluzioni Excel
  Visual Studio fornisce modelli di progetto che è possibile usare per creare personalizzazioni a livello di documento e componenti aggiuntivi VSTO per Microsoft Office Excel. È possibile usare queste soluzioni per automatizzare Excel, estenderne le funzionalità e personalizzarne l'interfaccia utente. Per altre informazioni sulle differenze tra le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Questo argomento contiene informazioni sui seguenti aspetti:

- [Automatizzare Excel](#automating).

- [Sviluppare personalizzazioni a livello di documento per Excel](#doclevel).

- [Sviluppare componenti aggiuntivi VSTO per Excel](#applevel).

- [Personalizzare l'interfaccia utente di Excel](#UI).

## <a name="automate-excel"></a><a name="automating"></a> Automatizzare Excel
 Il modello a oggetti di Excel espone diversi tipi che è possibile usare per automatizzare Excel. Ad esempio, è possibile creare grafici, formattare fogli di lavoro e impostare i valori degli intervalli e delle celle a livello di codice. Per altre informazioni, vedere [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md).

 Quando si sviluppano soluzioni Excel in Visual Studio, si possono anche usare *elementi host* e *controlli host* nelle soluzioni. Si tratta di oggetti che estendono alcuni oggetti di uso comune nel modello a oggetti di Excel, ad esempio gli oggetti <xref:Microsoft.Office.Interop.Excel.Worksheet> e <xref:Microsoft.Office.Interop.Excel.Range> . Gli oggetti estesi si comportano come gli oggetti di Excel sui quali si basano, ma aggiungono ulteriori eventi e funzionalità di data binding agli oggetti. Per altre informazioni, vedere [automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> Sviluppare personalizzazioni a livello di documento per Excel
 Una personalizzazione a livello di documento per Microsoft Office Excel è costituita da un assembly associato a una cartella di lavoro specifica. L'assembly in genere estende la cartella di lavoro personalizzando l'interfaccia utente e automatizzando Excel. Diversamente da un componente aggiuntivo VSTO a livello di applicazione, associato a Excel stesso, la funzionalità che si implementa in una personalizzazione è disponibile solo quando la cartella di lavoro associata è aperta in Excel.

 Per creare un progetto di personalizzazione a livello di documento per Excel, usare i modelli di progetto cartella di lavoro di Excel o modello di Excel nella finestra di dialogo **nuovo progetto** di Visual Studio. Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Per altre informazioni sul funzionamento delle personalizzazioni a livello di documento, vedere [architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Modello di programmazione della personalizzazione di Excel
 Quando si crea un progetto a livello di documento per Excel, in Visual Studio vengono generate diverse classi che costituiscono il fondamento della soluzione: `ThisWorkbook`, `Sheet1`, `Sheet2`e `Sheet3`. Queste classi rappresentano la cartella di lavoro e fogli di lavoro associati alla soluzione e forniscono un punto di partenza per la scrittura del codice.

 Per altre informazioni su queste classi generate e su altre funzionalità che è possibile usare in un progetto a livello di documento, vedere [programmare le personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> Sviluppare componenti aggiuntivi VSTO per Excel
 Un componente aggiuntivo VSTO per Microsoft Office Excel è costituito da un assembly caricato da Excel. L'assembly in genere estende Excel personalizzando l'interfaccia utente e automatizzando Excel. A differenza di una personalizzazione a livello di documento, associata a una cartella di lavoro specifica, la funzionalità implementata in un componente aggiuntivo VSTO non è limitata a una singola cartella di lavoro.

 Per creare un progetto di componente aggiuntivo VSTO per Excel, usare i modelli di progetto cartella di lavoro di Excel o modello di Excel nella finestra di dialogo **nuovo progetto** di Visual Studio. Per altre informazioni, vedere [procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Per informazioni generali sul funzionamento dei componenti aggiuntivi VSTO, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Modello di programmazione del componente aggiuntivo di Excel
 Quando si crea un progetto di componente aggiuntivo VSTO per Excel, Visual Studio genera una classe, chiamata `ThisAddIn`, che costituisce la base della soluzione. Questa classe fornisce un punto di partenza per la scrittura del codice ed espone anche il modello a oggetti di Excel nel componente aggiuntivo VSTO.

 Per altre informazioni sulla `ThisAddIn` classe e su altre funzionalità di Visual Studio che è possibile usare in un componente aggiuntivo VSTO, vedere [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> Personalizzare l'interfaccia utente di Excel
 Sono disponibili diverse modalità per personalizzare l'interfaccia utente di Excel. Alcune opzioni sono disponibili per tutti i tipi di progetto e altre opzioni sono disponibili solo per i componenti aggiuntivi VSTO o le personalizzazioni a livello di documento.

### <a name="options-for-all-project-types"></a>Opzioni per tutti i tipi di progetto
 La tabella seguente elenca le opzioni di personalizzazione disponibili per le personalizzazioni a livello di documento e i componenti aggiuntivi VSTO.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Personalizzare la barra multifunzione.|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Aggiungere controlli Windows Form o controlli estesi di Excel a un foglio di lavoro della cartella di lavoro personalizzata per una personalizzazione a livello di documento, o in qualsiasi cartella di lavoro aperta per un componente aggiuntivo VSTO.|[Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Procedura: aggiungere controlli Chart a fogli di foglio](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Procedura: aggiungere controlli ListObject a fogli di foglio](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Procedura: aggiungere controlli NamedRange a fogli di foglio](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Opzioni per le personalizzazioni a livello di documento
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per le personalizzazioni a livello di documento.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Aggiunta di un riquadro delle azioni alla cartella di lavoro.|[Panoramica del riquadro azioni](../vsto/actions-pane-overview.md)<br /><br /> [Procedura: aggiungere un riquadro azioni ai documenti di Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Aggiungere a un foglio di lavoro controlli di intervallo esteso mappati ai nodi XML.|[Procedura: aggiungere controlli XMLMappedRange a fogli di foglio](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Opzioni per i componenti aggiuntivi VSTO
 La tabella seguente elenca le opzioni di personalizzazione disponibili solo per i componenti aggiuntivi VSTO.

|Attività|Per ulteriori informazioni|
|----------|--------------------------|
|Creare un riquadro attività personalizzato.|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md) | Fornisce una panoramica dei tipi principali forniti dal modello a oggetti di Excel. |
| [Automatizzare Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md) | Fornisce informazioni sugli oggetti estesi (forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) che è possibile usare nelle soluzioni Excel. |
| [Globalizzazione e localizzazione di soluzioni Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Contiene considerazioni speciali per le soluzioni Excel eseguite in computer che hanno impostazioni di Windows non in inglese. |
| [Cenni preliminari sui controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md) | Descrive come è possibile aggiungere controlli Windows Form ai fogli di lavoro di Excel. |
| [Procedura dettagliata: creare la prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Illustra come creare una personalizzazione di base a livello di documento per Excel. |
| [Procedura dettagliata: creare il primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Mostra come creare un componente aggiuntivo VSTO di base per Excel. |
| [Procedura dettagliata: aggiungere controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Illustra come aggiungere un pulsante di Windows Form, <xref:Microsoft.Office.Tools.Excel.NamedRange>e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di esecuzione con un componente aggiuntivo VSTO. |
| [Informazioni sulla creazione di co-creazione e sui componenti aggiuntivi](./understanding-coauthoring-and-addins.md) | Descrive le rettifiche che potrebbero essere necessarie per le soluzioni per la creazione di una coautorizzazione. |
| [Excel 2010 nello sviluppo per Office](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Fornisce collegamenti ad articoli e documentazione di riferimento sullo sviluppo di soluzioni Excel. Gli articoli non sono specifici per lo sviluppo di Office usando Visual Studio. |
