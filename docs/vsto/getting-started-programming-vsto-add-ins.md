---
title: Introduzione a programming VSTO Add-ins
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b709012dafe0db3dcc0959908a1e6b4d9e07e21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788784"
---
# <a name="get-started-programming-vsto-add-ins"></a>Introduzione a programming VSTO Add-ins
  È possibile usare componenti aggiuntivi VSTO per automatizzare le applicazioni di Microsoft Office, estendere le funzionalità dell'applicazione e personalizzare l'interfaccia utente dell'applicazione. Per informazioni sulle differenze tra componenti aggiuntivi VSTO per altri tipi di soluzioni Office è possibile creare tramite Visual Studio, vedere [Cenni preliminari sullo sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Creare progetti di componente aggiuntivo VSTO
 Creare progetti di componente aggiuntivo VSTO usando uno dei modelli di progetto del componente aggiuntivo VSTO nella finestra di **nuovo progetto** nella finestra di dialogo. Questi modelli includono riferimenti dell'assembly e file di progetto necessari. Visual Studio offre modelli di progetto di componente aggiuntivo VSTO per la maggior parte delle applicazioni di Office.

 Per altre informazioni su come creare un progetto di componente aggiuntivo VSTO, vedere [come: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Per altre informazioni sui modelli di progetto, vedere [Cenni preliminari sui modelli di progetto di Office](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Sviluppare progetti di componente aggiuntivo VSTO
 Quando si crea un progetto di componente aggiuntivo VSTO, Visual Studio crea automaticamente un *ThisAddIn. vb* (nella [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) oppure *ThisAddIn.cs* (in c#) i file di codice. Questo file contiene il `ThisAddIn` (classe), che fornisce le basi per il componente aggiuntivo VSTO. È possibile usare i membri di questa classe per eseguire il codice quando il componente aggiuntivo VSTO viene caricato o scaricato, per accedere al modello a oggetti dell'applicazione host e per estendere le funzionalità dell'applicazione. Per altre informazioni, vedere [programma VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatizzare le applicazioni usando i modelli a oggetti
 I modelli a oggetti delle applicazioni di Microsoft Office espongono molti tipi per i quali è possibile eseguire la programmazione in un componente aggiuntivo VSTO. È possibile utilizzare questi tipi per automatizzare l'applicazione. Ad esempio, a livello di programmazione, è possibile creare e inviare un messaggio di posta elettronica in Outlook o è possibile aprire un documento e aggiungere contenuto in Word. Per altre informazioni su come accedere al modello a oggetti dell'applicazione host nel codice, vedere [programma VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

 Per altre informazioni sui modelli a oggetti di applicazioni specifiche di Microsoft Office, vedere gli argomenti seguenti:

- [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)

- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)

- [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)

- [Soluzioni InfoPath](../vsto/infopath-solutions.md)

- [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md)

- [Soluzioni Project](../vsto/project-solutions.md)

- [Panoramica del modello a oggetti Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personalizzare l'interfaccia utente delle applicazioni
 Esistono diversi modi per personalizzare l'interfaccia utente dell'applicazione host usando un componente aggiuntivo VSTO:

- Per Excel e Word, è possibile aggiungere controlli gestiti ai documenti. Per altre informazioni, vedere [estendere documenti Word e cartelle di lavoro di Excel in componenti aggiuntivi VSTO in fase di esecuzione](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Se l'applicazione la supporta, è possibile personalizzare la barra multifunzione. Per altre informazioni, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).

- Se l'applicazione lo supporta, è possibile creare un riquadro attività personalizzato. Per altre informazioni, vedere [riquadri attività personalizzati](../vsto/custom-task-panes.md).

- Per Outlook, è possibile creare un'area del modulo personalizzato. Per altre informazioni, vedere [aree del modulo Outlook creare](../vsto/creating-outlook-form-regions.md).

- Per tutte le applicazioni di Microsoft Office, è possibile visualizzare Windows Form nel componente aggiuntivo VSTO.

  Per altre informazioni su come personalizzare le applicazioni dell'interfaccia utente di Microsoft Office, vedere [personalizzazione dell'interfaccia utente Office](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Passaggi successivi
 Per informazioni su come creare componenti aggiuntivi VSTO, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Procedura dettagliata: Creare il primo aggiuntivo VSTO per Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Procedura dettagliata: Creare il primo aggiuntivo VSTO per Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Procedura dettagliata: Creare un componente aggiuntivo di VSTO per Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Queste procedure dettagliate presentano gli strumenti di sviluppo per Office disponibili in Visual Studio e il modello di programmazione per i componenti aggiuntivi VSTO.

  Per un elenco di argomenti che illustrano alcune delle attività comuni nei progetti di Office, vedere [attività comuni nella programmazione Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Iniziare a usare &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Scrivere il codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)
- [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)
