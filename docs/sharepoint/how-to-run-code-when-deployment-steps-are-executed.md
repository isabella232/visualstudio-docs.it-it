---
title: 'Procedura: eseguire codice quando la distribuzione vengono eseguiti i passaggi | Microsoft Docs'
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
ms.openlocfilehash: cebd88cc49afa1092dfcd1d67ffdbf0fa3567ad0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119155"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Procedura: eseguire codice quando vengono eseguiti i passaggi di distribuzione
  Se si desidera eseguire attività aggiuntive per un passaggio di distribuzione in un progetto SharePoint, è possibile gestire gli eventi che vengono generati da elementi di progetto SharePoint prima e dopo ogni passaggio di distribuzione eseguiti in Visual Studio. Per altre informazioni, vedere [estendendo SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Per eseguire codice quando vengono eseguiti i passaggi di distribuzione  
  
1.  Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:  
  
    -   [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Per l'estensione, gestire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventi di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto (in un'estensione di elemento di progetto o l'estensione di progetto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto (in una definizione di un nuovo tipo di elemento di progetto).  
  
3.  Nell'evento gestori eventi, usare il <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> e <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parametri per ottenere informazioni sul passaggio della distribuzione. Ad esempio, è possibile determinare il passaggio di distribuzione è in esecuzione e indica se la soluzione viene distribuito o ritratto.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come gestire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventi in un'estensione per l'elemento di progetto di un'istanza di elenco. Questa estensione scrive un messaggio aggiuntivo per il **Output** finestra quando Visual Studio viene riciclato il pool di applicazioni durante la distribuzione e il ritiro della soluzione.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Distribuire l'estensione  
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Procedura: eseguire codice quando viene distribuito o ritratto un progetto SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  
