---
title: Eseguire codice quando SharePoint progetto viene distribuito o ritirato
titleSuffix: ''
description: Informazioni su come eseguire codice quando un progetto SharePoint viene distribuito o ritirato in modo da poter gestire gli eventi generati da Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 76edd5250d0876a0e7ac8dfafb1d03f00dc5c89f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156357"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Procedura: Eseguire codice quando un SharePoint viene distribuito o ritirato
  Se si desidera eseguire attività aggiuntive quando un progetto SharePoint viene distribuito o ritirato, è possibile gestire gli eventi generati da Visual Studio. Per altre informazioni, vedere [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Per eseguire codice quando un SharePoint viene distribuito o ritirato

1. Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

   - [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Procedura: Definire un tipo di SharePoint di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Nell'estensione accedere <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> all'oggetto . Per altre informazioni, vedere [Procedura: Recuperare il SharePoint servizio di progetto](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> e dell'servizio di progetto.

4. Nei gestori eventi usare il parametro <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> per ottenere informazioni sulla sessione di distribuzione corrente. Ad esempio, è possibile determinare quale progetto si trova nella sessione di distribuzione corrente e se viene distribuito o ritirato.

   Nell'esempio di codice seguente viene illustrato come gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> eventi e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> in un'estensione di progetto. Questa estensione scrive un messaggio aggiuntivo nella finestra **Output** all'avvio e al completamento della distribuzione per un SharePoint progetto.

   :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs" id="Snippet12":::
   :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb" id="Snippet12":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Procedura: Eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
