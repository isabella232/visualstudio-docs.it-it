---
title: Uso del SharePoint Project di | Microsoft Docs
description: Usare il SharePoint servizio di progetto per eseguire attività correlate al sistema del progetto. Visualizzare un elenco di servizio di progetto funzionalità.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f1edd12c7ca1fef8586ffdde6ee52ae2abd3eb29e90ae49641735f4197fe98bb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409358"
---
# <a name="use-the-sharepoint-project-service"></a>Usare il SharePoint servizio di progetto
  Il sistema di progetti SharePoint include un servizio progetto che può essere usato per eseguire attività correlate al sistema di progetti. Il servizio progetto è un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.

 È possibile accedere al servizio progetto di SharePoint in qualsiasi estensione degli strumenti di SharePoint. È anche possibile accedervi in altri tipi di estensioni di Visual Studio, ad esempio i componenti aggiuntivi e i package VS. Per altre informazioni, vedere [Procedura: Recuperare il SharePoint servizio di progetto](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Project funzionalità del servizio
 La tabella seguente elenca le attività che è possibile eseguire usando il servizio progetto di SharePoint e il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> o la proprietà da usare per eseguire ogni attività.

|Attività|Membro da usare|
|----------|-------------------|
|Accesso a qualsiasi progetto SharePoint aperto in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|
|Accesso a tutti i tipi di elementi del progetto SharePoint disponibili (inclusi i tipi di elementi incorporati e personalizzati del progetto).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|
|Accesso a tutti i passaggi di distribuzione disponibili per i progetti SharePoint (inclusi i passaggi di distribuzione incorporati e personalizzati).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|
|Accesso agli eventi generati quando uno sviluppatore effettua il refactoring del codice in un progetto SharePoint.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|
|Eseguire un comando *SharePoint personalizzato che* chiama nel SharePoint a oggetti del server. Per altre informazioni sui SharePoint, vedere Chiamare nei modelli [SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|
|Conversione di un tipo del sistema del progetto SharePoint in un tipo del modello a oggetti di automazione o di integrazione di Visual Studio e viceversa. Per altre informazioni, vedere [Convert between SharePoint project system types and other Visual Studio project types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Metodo<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> .|
|Scrivere messaggi nella finestra **Output** o **nella finestra Elenco** errori in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|
|Accesso ad altri servizi disponibili in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|
|Recupero del percorso della cartella di installazione del sito di SharePoint locale usato per il debug della soluzione.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|
|Determinazione dell'installazione di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] nel computer.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|
|Convalida di una funzionalità o un pacchetto in una soluzione SharePoint.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|

## <a name="see-also"></a>Vedi anche
- [Eseguire la conversione SharePoint tipi di sistema del progetto e altri Visual Studio di progetto](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Procedura: Recuperare il SharePoint servizio di progetto](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Estendere gli SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Panoramica del modello di programmazione delle estensioni SharePoint tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Procedura: Ottenere un servizio dall'oggetto DTE](/previous-versions/bb166401(v=vs.140))