---
title: 'Procedura: eseguire codice quando un progetto SharePoint viene distribuito o ritratto | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4fa7d2652e65e26686a5058fcb2c8f5130fbbdde
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119180"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Procedura: eseguire codice quando viene distribuito o ritratto un progetto SharePoint
  Se si desidera eseguire attività aggiuntive quando viene distribuito o ritratto un progetto SharePoint, è possibile gestire gli eventi generati da Visual Studio. Per altre informazioni, vedere [estendere SharePoint packaging e la distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Per eseguire codice quando un progetto SharePoint viene distribuito o ritratto  
  
1.  Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
    -   [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Nell'estensione di accesso di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto. Per altre informazioni, vedere [procedura: recuperare il servizio di progetto SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Gestire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> gli eventi del servizio di progetto.  
  
4.  Nei gestori eventi, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> parametro per ottenere informazioni relative alla sessione di distribuzione corrente. Ad esempio, è possibile determinare quale progetto si trova nella sessione di distribuzione corrente e se viene distribuito o ritratto.  
  
 Esempio di codice seguente viene illustrato come gestire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventi in un'estensione di progetto. Questa estensione scrive un messaggio aggiuntivo per il **Output** finestra quando la distribuzione viene avviata e completata per un progetto SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Distribuire l'estensione  
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Procedura: eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
