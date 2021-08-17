---
title: Funzionalità disponibili in base Office'applicazione e al tipo di progetto
description: Informazioni su Visual Studio diversi tipi di modelli di progetto che supportano scenari aziendali diversi per Microsoft Office applicazioni.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: bb532244198a26da0106652f3c1167ef111c91ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106354"
---
# <a name="features-available-by-office-application-and-project-type"></a>Funzionalità disponibili in base Office'applicazione e al tipo di progetto
  In Visual Studio sono disponibili numerosi tipi di modelli di progetto che supportano scenari aziendali diversi per le applicazioni di Microsoft Office, inclusi i tipi seguenti:

- Personalizzazioni a livello di documento.

- Componenti aggiuntivi VSTO.

  Non tutte le applicazioni possono utilizzare ogni tipo di progetto. Ad esempio, i progetti a livello di documento sono disponibili solo per Microsoft Office Word e Microsoft Office Excel. Analogamente, alcune funzionalità sono disponibili solo per determinati tipi di progetti o applicazioni. Ad esempio, il riquadro azioni è disponibile solo nei progetti a livello di documento e le estensioni della barra multifunzione sono disponibili solo per alcune applicazioni. Per altre informazioni sui diversi tipi di progetto, vedere panoramica Office [sviluppo di ](../vsto/office-solutions-development-overview-vsto.md)soluzioni &#40;VSTO&#41;.

> [!NOTE]
> Modelli di progetto di Office sono disponibili solo in alcune edizioni di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [Configurare un computer per sviluppare Office soluzioni](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Project disponibili per applicazioni Microsoft Office diverse
 Nella tabella seguente sono indicate le applicazioni che è possibile utilizzare con ogni tipo di progetto.

|Tipi di progetto|Applicazione Microsoft Office|
|-------------------|----------------------------------|
|Personalizzazioni a livello di documento|Excel<br /><br /> Word|
|Componenti aggiuntivi VSTO|Excel<br /><br /> InfoPath (solo InfoPath 2013 e InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Funzionalità disponibili in tipi di progetto diversi
 Nella tabella seguente sono indicati i tipi di progetto che forniscono ciascuna funzionalità.

|Funzionalità|Tipi di progetto che forniscono la funzionalità|Altre informazioni|
|-------------|--------------------------------------------|---------------------|
|Riquadro azioni.|Progetti a livello di documento.|[Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)|
|Distribuzione ClickOnce.|Progetti a livello di documento e VS.|[Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)|
|Riquadri attività personalizzati.|Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> - Excel<br />- InfoPath (solo InfoPath 2013 e InfoPath 2010)<br />- Outlook<br />- PowerPoint<br />- Parola|[Riquadri attività personalizzati](../vsto/custom-task-panes.md)|
|Parti XML personalizzate.|Progetti a livello di documento.<br /><br /> Progetti di livello applicazione per le applicazioni seguenti:<br /><br /> - Excel<br />- PowerPoint<br />- Parola|[Panoramica delle parti XML personalizzate](../vsto/custom-xml-parts-overview.md)|
|Cache dei dati.|Progetti a livello di documento.|[Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)|
|Esporre un oggetto in un VSTO componente aggiuntivo ad altre Microsoft Office soluzioni.|Progetti di componente aggiuntivo VSTO.|[Chiamare il codice VSTO componenti aggiuntivi da altre Office soluzioni](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|I controlli host seguenti:<br /><br /> - Grafico<br />- ListObject<br />- NamedRange<br />- Controlli contenuto<br />- Segnalibro|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per Word ed Excel.|[Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)|
|I controlli host seguenti:<br /><br /> - XMLMappedRange<br />- XMLNode<br />- XMLNodes|Progetti a livello di documento.|[Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)|
|Distribuzione di più progetti.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: Distribuire più soluzioni Office in un unico programma di ClickOnce installazione](/previous-versions/dd465290(v=vs.110))|
|Aree di modulo di Outlook.|Progetti di componente aggiuntivo VSTO per Outlook.|[Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)|
|Azioni di post-distribuzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO.|[Procedura dettagliata: Copiare un documento nel computer dell'utente finale dopo un ClickOnce installazione](/previous-versions/dd465291(v=vs.110))|
|Personalizzazioni della barra multifunzione.|Progetti a livello di documento.<br /><br /> Progetti di componente aggiuntivo VSTO per le applicazioni seguenti:<br /><br /> - Excel<br />- InfoPath (solo InfoPath 2013 e InfoPath 2010)<br />- Outlook<br />- PowerPoint<br />- Project<br />- Visio<br />- Parola|[Panoramica della barra multifunzione](../vsto/ribbon-overview.md)|
|Programma di creazione documenti visivi.|Progetti a livello di documento.|[Office progetti nell'ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>Vedi anche
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office panoramica dello sviluppo di soluzioni &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Panoramica del riquadro Azioni](../vsto/actions-pane-overview.md)
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)