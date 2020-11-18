---
title: 'Convert: tipi di sistema del progetto SharePoint in/da altri tipi'
titleSuffix: ''
description: Eseguire la conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio. Vedere un elenco che descrive in dettaglio i tipi che possono essere convertiti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75f8a2072e81936c4c1c691261e301aae37b0191
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850481"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio
  In alcuni casi è possibile disporre di un oggetto nel sistema del progetto SharePoint e si desidera utilizzare le funzionalità di un oggetto corrispondente nel modello a oggetti di automazione di Visual Studio o nel modello a oggetti di integrazione o viceversa. In questi casi, è possibile utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo del servizio di progetto SharePoint per convertire l'oggetto in un modello a oggetti diverso.

 È ad esempio possibile disporre di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto, ma si desidera utilizzare metodi disponibili solo su un <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> oggetto o. In questo caso, è possibile usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire l'oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> in un oggetto <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Per altre informazioni sul modello a oggetti di automazione di Visual Studio e sul modello a oggetti di integrazione di Visual Studio, vedere [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Tipi di conversioni
 Nella tabella seguente sono elencati i tipi che questo metodo può convertire tra il sistema del progetto SharePoint e gli altri modelli a oggetti di Visual Studio.

|Tipo di sistema del progetto SharePoint|Tipi corrispondenti nei modelli a oggetti di automazione e integrazione|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> o<br /><br /> Qualsiasi interfaccia nel modello a oggetti di integrazione di Visual Studio implementata dall'oggetto COM sottostante per il progetto. Queste interfacce includono <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> o un'interfaccia derivata, e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Per un elenco delle interfacce principali implementate dai progetti, vedere componenti di [base del modello di progetto](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> o<br /><br /> <xref:System.UInt32>Valore (detto anche VSITEMID) che identifica il membro del progetto nell'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> che lo contiene. Questo valore può essere passato al parametro *ItemId* di alcuni <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi.|

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto in un oggetto <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 L'esempio presenta i requisiti seguenti:

- Estensione del sistema del progetto SharePoint con un riferimento all'assembly *EnvDTE.dll* . Per ulteriori informazioni, vedere [estensione del sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Codice che registra il `projectService_ProjectAdded` metodo per gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per un esempio, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vedere anche

- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
