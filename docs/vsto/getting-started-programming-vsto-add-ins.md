---
title: Introduzione alla programmazione dei componenti aggiuntivi VSTO
description: Informazioni su come usare i componenti aggiuntivi VSTO per automatizzare Microsoft Office applicazioni, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848292"
---
# <a name="get-started-programming-vsto-add-ins"></a>Introduzione alla programmazione dei componenti aggiuntivi VSTO
> [!IMPORTANT]
> VSTO si basa [sull'.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). I componenti aggiuntivi COM possono anche essere scritti con il .NET Framework. Non è possibile creare componenti aggiuntivi di Office con [.NET Core e .NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five), le versioni più recenti di .NET. Questo perché .NET Core/.NET 5+ non può funzionare con .NET Framework nello stesso processo e può causare errori di caricamento dei componenti aggiuntivi. È possibile continuare a usare .NET Framework per scrivere componenti aggiuntivi VSTO e COM per Office. Microsoft non aggiorerà VSTO o la piattaforma del componente aggiuntivo COM per usare .NET Core o .NET 5+. È possibile sfruttare .NET Core e .NET 5+, incluso ASP.NET Core, per creare il lato server dei componenti aggiuntivi [Web di Office.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  È possibile usare componenti aggiuntivi VSTO per automatizzare le applicazioni di Microsoft Office, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione. Per informazioni sul confronto tra i componenti aggiuntivi VSTO e altri tipi di soluzioni Office che è possibile creare usando Visual Studio, vedere Panoramica dello sviluppo di soluzioni Office &#40;[VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Creare progetti di componente aggiuntivo VSTO
 Creare progetti di componente aggiuntivo VSTO usando uno dei modelli di progetto del componente aggiuntivo VSTO nella **finestra di dialogo** Nuovo progetto . Questi modelli includono riferimenti dell'assembly e file di progetto necessari. Visual Studio offre modelli di progetto di componente aggiuntivo VSTO per la maggior parte delle applicazioni di Office.

 Per altre informazioni su come creare un progetto di componente aggiuntivo VSTO, vedere [Procedura: Creare](../vsto/how-to-create-office-projects-in-visual-studio.md)progetti di Office in Visual Studio . Per altre informazioni sui modelli di progetto, vedere Panoramica [dei modelli di progetto di Office.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Sviluppare progetti di componenti aggiuntivi VSTO
 Quando si crea un progetto di componente aggiuntivo VSTO, Visual Studio crea automaticamente un file di codice *ThisAddIn.vb* (in ) o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (in C#). Questo file contiene la `ThisAddIn` classe , che fornisce le basi per il componente aggiuntivo VSTO. È possibile usare i membri di questa classe per eseguire il codice quando il componente aggiuntivo VSTO viene caricato o scaricato, per accedere al modello a oggetti dell'applicazione host e per estendere le funzionalità dell'applicazione. Per altre informazioni, vedere [Programmare componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatizzare le applicazioni usando i modelli a oggetti
 I modelli a oggetti delle applicazioni di Microsoft Office espongono molti tipi per i quali è possibile eseguire la programmazione in un componente aggiuntivo VSTO. È possibile utilizzare questi tipi per automatizzare l'applicazione. Ad esempio, a livello di programmazione, è possibile creare e inviare un messaggio di posta elettronica in Outlook o è possibile aprire un documento e aggiungere contenuto in Word. Per altre informazioni su come accedere al modello a oggetti dell'applicazione host nel codice, vedere Programmare componenti aggiuntivi [VSTO.](../vsto/programming-vsto-add-ins.md)

 Per altre informazioni sui modelli a oggetti di applicazioni specifiche di Microsoft Office, vedere gli argomenti seguenti:

- [Panoramica del modello a oggetti di Excel](../vsto/excel-object-model-overview.md)

- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)

- [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)

- [Soluzioni InfoPath](../vsto/infopath-solutions.md)

- [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md)

- [Soluzioni di progetto](../vsto/project-solutions.md)

- [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personalizzare l'interfaccia utente delle applicazioni
 Esistono diversi modi per personalizzare l'interfaccia utente dell'applicazione host usando un componente aggiuntivo VSTO:

- Per Excel e Word, è possibile aggiungere controlli gestiti ai documenti. Per altre informazioni, vedere Estendere documenti di Word e cartelle di lavoro [di Excel nei componenti aggiuntivi VSTO in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

- Se l'applicazione la supporta, è possibile personalizzare la barra multifunzione. Per altre informazioni, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

- Se l'applicazione lo supporta, è possibile creare un riquadro attività personalizzato. Per altre informazioni, vedere [Riquadri attività personalizzati.](../vsto/custom-task-panes.md)

- Per Outlook, è possibile creare un'area del modulo personalizzato. Per altre informazioni, vedere Creare [aree del modulo di Outlook.](../vsto/creating-outlook-form-regions.md)

- Per tutte le applicazioni di Microsoft Office, è possibile visualizzare Windows Form nel componente aggiuntivo VSTO.

  Per altre informazioni su come personalizzare l'interfaccia utente delle applicazioni Microsoft Office, vedere Personalizzazione dell'interfaccia [utente di Office.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare componenti aggiuntivi VSTO, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Creare il primo componente aggiuntivo VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Procedura dettagliata: Creare la prima Add-In VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Procedura dettagliata: Creare il primo componente aggiuntivo VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Procedura dettagliata: Creare il primo componente aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Procedura dettagliata: Creare il primo componente aggiuntivo VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Queste procedure dettagliate presentano gli strumenti di sviluppo per Office disponibili in Visual Studio e il modello di programmazione per i componenti aggiuntivi VSTO.

  Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Office, vedere [Attività comuni nella programmazione di Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introduzione allo &#40;di Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Scrivere codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Programmare componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)
