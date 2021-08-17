---
title: 'Converti: SharePoint tipi di sistema del progetto in/da altri tipi'
titleSuffix: ''
description: Eseguire la conversione SharePoint tipi di sistema del progetto e altri Visual Studio tipi di progetto. Vedere un elenco che elenca in dettaglio i tipi che possono essere convertiti.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c6624295dfb43a15a9ae2235b15a658de4eea76d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106861"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Eseguire la conversione SharePoint tipi di sistema del progetto e altri Visual Studio tipi di progetto
  In alcuni casi potrebbe essere presente un oggetto nel sistema del progetto SharePoint e si vogliono usare le funzionalità di un oggetto corrispondente nel modello a oggetti di automazione di Visual Studio o nel modello a oggetti di integrazione o viceversa. In questi casi, è possibile usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo dell'SharePoint servizio di progetto per convertire l'oggetto in un modello a oggetti diverso.

 Ad esempio, potrebbe essere disponibile un oggetto , ma si vogliono usare metodi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> disponibili solo in un oggetto o <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . In questo caso, è possibile usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> metodo per convertire in o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Per altre informazioni sul modello Visual Studio a oggetti di automazione di Visual Studio e sul modello a oggetti di integrazione di Visual Studio, vedere Panoramica del modello di programmazione delle [estensioni degli](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)strumenti di SharePoint .

## <a name="types-of-conversions"></a>Tipi di conversioni
 Nella tabella seguente sono elencati i tipi che questo metodo può convertire tra il SharePoint di progetto di e gli altri Visual Studio a oggetti.

|SharePoint di sistema del progetto|Tipi corrispondenti nei modelli a oggetti di automazione e integrazione|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> oppure<br /><br /> Qualsiasi interfaccia nel Visual Studio a oggetti di integrazione implementata dall'oggetto COM sottostante per il progetto. Queste interfacce includono <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (o un'interfaccia derivata) e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Per un elenco delle interfacce principali implementate dai progetti, vedere Project [Componenti di base del modello.](../extensibility/internals/project-model-core-components.md)|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> oppure<br /><br /> Valore <xref:System.UInt32> (denominato anche VSITEMID) che identifica il membro del progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> nell'oggetto che lo contiene. Questo valore può essere passato al *parametro itemid* di alcuni <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi.|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come utilizzare <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> il metodo per convertire un oggetto in un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> .

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs" id="Snippet2":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb" id="Snippet2":::

 L'esempio presenta i requisiti seguenti:

- Estensione del sistema SharePoint progetto che contiene un riferimento all'assembly *EnvDTE.dll* assembly. Per altre informazioni, vedere [Estendere il SharePoint del progetto.](../sharepoint/extending-the-sharepoint-project-system.md)

- Codice che registra il metodo `projectService_ProjectAdded` per gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> l'evento di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per un esempio, vedere [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vedi anche

- [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md)
- [Procedura: Recuperare il SharePoint servizio di progetto](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Panoramica del modello di programmazione delle estensioni SharePoint strumenti](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
