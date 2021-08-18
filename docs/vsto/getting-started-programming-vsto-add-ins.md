---
title: Introduzione alla programmazione VSTO componenti aggiuntivi
description: Informazioni su come usare VSTO componenti aggiuntivi per automatizzare Microsoft Office applicazioni, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 65ccd3385ca33e098eb5cec073ea56fd742e4d65
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130520"
---
# <a name="get-started-programming-vsto-add-ins"></a>Introduzione alla programmazione VSTO componenti aggiuntivi
> [!IMPORTANT]
> VSTO si basa sull'.NET Framework [.](https://docs.microsoft.com/dotnet/framework/get-started/overview) I componenti aggiuntivi COM possono anche essere scritti con il .NET Framework. Office Non è possibile creare componenti aggiuntivi con [.NET Core e .NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five), le versioni più recenti di .NET. Ciò è dovuto al fatto che .NET Core/.NET 5+ non può funzionare con .NET Framework nello stesso processo e può causare errori di caricamento dei componenti aggiuntivi. È possibile continuare a usare .NET Framework per scrivere VSTO e componenti aggiuntivi COM per Office. Microsoft non aggiorerà VSTO piattaforma del componente aggiuntivo COM per usare .NET Core o .NET 5+. È possibile sfruttare .NET Core e .NET 5+, incluso ASP.NET Core, per creare il lato server di Office [componenti aggiuntivi Web.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  È possibile usare componenti aggiuntivi VSTO per automatizzare le applicazioni di Microsoft Office, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione. Per informazioni sul confronto VSTO componenti aggiuntivi con altri tipi di soluzioni Office che è possibile creare usando Visual Studio, vedere Office [solutions development overview &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Creare VSTO di componenti aggiuntivi
 Creare VSTO progetti di componente aggiuntivo usando uno dei modelli di progetto VSTO componente aggiuntivo nella finestra di dialogo **Nuovo Project.** Questi modelli includono riferimenti dell'assembly e file di progetto necessari. Visual Studio offre modelli di progetto di componente aggiuntivo VSTO per la maggior parte delle applicazioni di Office.

 Per altre informazioni su come creare un progetto VSTO componente aggiuntivo, vedere [Procedura:](../vsto/how-to-create-office-projects-in-visual-studio.md)Creare Office progetti in Visual Studio . Per altre informazioni sui modelli di progetto, vedere panoramica Office [dei modelli di progetto.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Sviluppare VSTO di componenti aggiuntivi
 Quando si crea un VSTO di componente aggiuntivo, Visual Studio crea automaticamente un file di codice *ThisAddIn.vb* (in ) o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (in C#). Questo file contiene la `ThisAddIn` classe , che fornisce le basi per il componente VSTO componente aggiuntivo. È possibile usare i membri di questa classe per eseguire il codice quando il componente aggiuntivo VSTO viene caricato o scaricato, per accedere al modello a oggetti dell'applicazione host e per estendere le funzionalità dell'applicazione. Per altre informazioni, vedere [Programmi VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatizzare le applicazioni usando i modelli a oggetti
 I modelli a oggetti delle applicazioni di Microsoft Office espongono molti tipi per i quali è possibile eseguire la programmazione in un componente aggiuntivo VSTO. È possibile utilizzare questi tipi per automatizzare l'applicazione. Ad esempio, a livello di programmazione, è possibile creare e inviare un messaggio di posta elettronica in Outlook o è possibile aprire un documento e aggiungere contenuto in Word. Per altre informazioni su come accedere al modello a oggetti dell'applicazione host nel codice, vedere Programmi [VSTO componenti aggiuntivi](../vsto/programming-vsto-add-ins.md).

 Per altre informazioni sui modelli a oggetti di applicazioni specifiche di Microsoft Office, vedere gli argomenti seguenti:

- [Excel panoramica del modello a oggetti](../vsto/excel-object-model-overview.md)

- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)

- [Outlook panoramica del modello a oggetti](../vsto/outlook-object-model-overview.md)

- [Soluzioni InfoPath](../vsto/infopath-solutions.md)

- [PowerPoint soluzioni](../vsto/powerpoint-solutions.md)

- [Project soluzioni](../vsto/project-solutions.md)

- [Visio panoramica del modello a oggetti](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personalizzare l'interfaccia utente delle applicazioni
 Esistono diversi modi per personalizzare l'interfaccia utente dell'applicazione host usando un VSTO componente aggiuntivo:

- Per Excel e Word, è possibile aggiungere controlli gestiti ai documenti. Per altre informazioni, vedere Estendere documenti di Word Excel cartelle di lavoro in VSTO [componenti aggiuntivi in fase di esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

- Se l'applicazione la supporta, è possibile personalizzare la barra multifunzione. Per altre informazioni, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

- Se l'applicazione lo supporta, è possibile creare un riquadro attività personalizzato. Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).

- Per Outlook, è possibile creare un'area del modulo personalizzato. Per altre informazioni, vedere [Creare aree Outlook modulo](../vsto/creating-outlook-form-regions.md).

- Per tutte le applicazioni di Microsoft Office, è possibile visualizzare Windows Form nel componente aggiuntivo VSTO.

  Per altre informazioni su come personalizzare l'interfaccia utente delle applicazioni Microsoft Office, vedere Office [personalizzazione dell'interfaccia utente](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare componenti aggiuntivi VSTO, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Procedura dettagliata: Creare la prima VSTO Add-In per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Procedura dettagliata: Creare il primo VSTO componente aggiuntivo per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Queste procedure dettagliate presentano gli strumenti di sviluppo per Office disponibili in Visual Studio e il modello di programmazione per i componenti aggiuntivi VSTO.

  Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti Office, vedere [Attività comuni nella](../vsto/common-tasks-in-office-programming.md)programmazione Office .

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare progetti Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introduzione allo &#40;Office sviluppo in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Scrivere codice in Office soluzioni](../vsto/writing-code-in-office-solutions.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
