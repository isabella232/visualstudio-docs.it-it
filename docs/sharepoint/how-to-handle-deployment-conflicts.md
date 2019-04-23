---
title: 'Procedura: Gestire i conflitti di distribuzione | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62e7740915d341eee1bbf5e112c4f09297c98be1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066143"
---
# <a name="how-to-handle-deployment-conflicts"></a>Procedura: Gestire i conflitti di distribuzione
  È possibile fornire il proprio codice per gestire i conflitti di distribuzione per un elemento di progetto SharePoint. Ad esempio, si potrebbe determinare se tutti i file nell'elemento di progetto corrente esistono già nel percorso di distribuzione e quindi eliminare i file distribuiti prima di distribuita l'elemento del progetto corrente. Per altre informazioni sui conflitti di distribuzione, vedere [estendendo SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Per gestire un conflitto di distribuzione

1. Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

    - [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Per l'estensione, gestire le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> eventi di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto (in un'estensione di elemento di progetto o l'estensione di progetto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto (in una definizione di un nuovo tipo di elemento di progetto).

3. Nel gestore dell'evento, determinare se si verifica un conflitto tra l'elemento del progetto in fase di distribuzione e la soluzione distribuita nel sito di SharePoint, in base ai criteri che si applicano al proprio scenario. È possibile usare il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> proprietà del parametro di argomenti dell'evento per analizzare l'elemento del progetto che viene distribuita ed è possibile analizzare i file nel percorso di distribuzione chiamando un comando di SharePoint definite per questo scopo.

     Per molti tipi di conflitti, è innanzitutto possibile determinare il passaggio di distribuzione è in esecuzione. È possibile farlo usando il <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> proprietà del parametro di argomenti dell'evento. Anche se è in genere opportuno per rilevare i conflitti durante l'elemento predefinito <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> passaggio di distribuzione, è possibile cercare i conflitti durante tutti i passaggi di distribuzione.

4. Se si verifica un conflitto, usare il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metodo per il <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> proprietà degli argomenti dell'evento per creare un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto. Questo oggetto rappresenta il conflitto di distribuzione. Nella chiamata al <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> (metodo), specificare anche il metodo che viene chiamato per risolvere il conflitto.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato il processo di base per la gestione di un conflitto di distribuzione in un'estensione di elemento di progetto per gli elementi di progetto di definizione di elenco. Per gestire un conflitto di distribuzione per un tipo di elemento di progetto diverso, passare una stringa diversa per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Per altre informazioni, vedere [elementi di progetto SharePoint estendere](../sharepoint/extending-sharepoint-project-items.md).

 Per semplicità, il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> gestore dell'evento in questo esempio si presuppone che esista un conflitto di distribuzione (vale a dire, sempre aggiunto un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto) e il `Resolve` metodo restituisce semplicemente **true** per indicare che il conflitto è stato risolto. In uno scenario reale, il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> gestore dell'evento potrebbe determinare innanzitutto se esiste un conflitto tra un file nell'elemento di progetto corrente e un file nel percorso di distribuzione e quindi aggiungere un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto solo se si verifica un conflitto. Ad esempio, è possibile utilizzare il `e.ProjectItem.Files` proprietà nel gestore eventi per analizzare i file nell'elemento del progetto e si potrebbe chiamare un comando di SharePoint per analizzare i file nel percorso di distribuzione. Analogamente, in uno scenario reale il `Resolve` metodo può chiamare un comando di SharePoint per risolvere il conflitto nel sito di SharePoint. Per altre informazioni sulla creazione di comandi di SharePoint, vedere [come: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuire l'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Estendere la distribuzione e creazione di pacchetti di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendere gli elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura: Eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Procedura: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
