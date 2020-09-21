---
title: Utilizzo del servizio di progetto SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3aeee895810eed8e434fda93328e4e179c9d39
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740110"
---
# <a name="use-the-sharepoint-project-service"></a>Usare il servizio di progetto SharePoint
  Il sistema di progetti SharePoint include un servizio progetto che può essere usato per eseguire attività correlate al sistema di progetti. Il servizio progetto è un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.

 È possibile accedere al servizio progetto di SharePoint in qualsiasi estensione degli strumenti di SharePoint. È anche possibile accedervi in altri tipi di estensioni di Visual Studio, ad esempio i componenti aggiuntivi e i package VS. Per ulteriori informazioni, vedere [procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Funzionalità del servizio di progetto
 La tabella seguente elenca le attività che è possibile eseguire usando il servizio progetto di SharePoint e il metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> o la proprietà da usare per eseguire ogni attività.

|Attività|Membro da usare|
|----------|-------------------|
|Accesso a qualsiasi progetto SharePoint aperto in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|
|Accesso a tutti i tipi di elementi del progetto SharePoint disponibili (inclusi i tipi di elementi incorporati e personalizzati del progetto).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|
|Accesso a tutti i passaggi di distribuzione disponibili per i progetti SharePoint (inclusi i passaggi di distribuzione incorporati e personalizzati).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|
|Accesso agli eventi generati quando uno sviluppatore effettua il refactoring del codice in un progetto SharePoint.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|
|Eseguire un *comando di SharePoint* personalizzato che effettua chiamate nel modello a oggetti del server SharePoint. Per ulteriori informazioni sui comandi di SharePoint, vedere la pagina relativa [alla chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|
|Conversione di un tipo del sistema del progetto SharePoint in un tipo del modello a oggetti di automazione o di integrazione di Visual Studio e viceversa. Per altre informazioni, vedere eseguire la [conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Metodo<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> .|
|Scrivere messaggi nella finestra di **output** o **Elenco errori** finestra in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|
|Accesso ad altri servizi disponibili in Visual Studio.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|
|Recupero del percorso della cartella di installazione del sito di SharePoint locale usato per il debug della soluzione.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|
|Determinazione dell'installazione di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] nel computer.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|
|Convalida di una funzionalità o un pacchetto in una soluzione SharePoint.|Proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|

## <a name="see-also"></a>Vedere anche
- [Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Procedura: Ottenere un servizio dall'oggetto DTE](/previous-versions/bb166401(v=vs.140))