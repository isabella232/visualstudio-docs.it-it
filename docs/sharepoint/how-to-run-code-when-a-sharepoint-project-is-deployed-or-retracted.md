---
title: Eseguire codice quando il progetto SharePoint viene distribuito o ritratto
titleSuffix: ''
description: Informazioni su come eseguire il codice quando un progetto SharePoint viene distribuito o ritratto per poter gestire gli eventi generati da Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4645d0b2cf1670a3834c4ac09cd66d56b48fbf27
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214473"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Procedura: eseguire codice quando un progetto SharePoint viene distribuito o ritratto
  Se si desidera eseguire attività aggiuntive quando un progetto SharePoint viene distribuito o ritratto, è possibile gestire gli eventi generati da Visual Studio. Per ulteriori informazioni, vedere [estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Per eseguire il codice quando un progetto SharePoint viene distribuito o ritratto

1. Creare un'estensione di elemento del progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

   - [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Nell'estensione accedere all' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per ulteriori informazioni, vedere [procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventi e del servizio del progetto.

4. Nei gestori eventi, usare il <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> parametro per ottenere informazioni sulla sessione di distribuzione corrente. Ad esempio, è possibile determinare quale progetto si trova nella sessione di distribuzione corrente e se viene distribuito o ritratto.

   Nell'esempio di codice riportato di seguito viene illustrato come gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventi e in un'estensione di progetto. Questa estensione scrive un ulteriore messaggio nella finestra di **output** all'avvio e al completamento della distribuzione per un progetto SharePoint.

   :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs" id="Snippet12":::
   :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Procedura: eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
