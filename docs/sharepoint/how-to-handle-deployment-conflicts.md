---
title: 'Procedura: Gestire i conflitti di distribuzione | Microsoft Docs'
description: Vedere un esempio di come implementare il proprio codice per gestire i conflitti di distribuzione per un SharePoint di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8da6e8bd908466b8314ab9ff6cf3e9d998644a77
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047699"
---
# <a name="how-to-handle-deployment-conflicts"></a>Procedura: Gestire i conflitti di distribuzione
  È possibile fornire il proprio codice per gestire i conflitti di distribuzione per un SharePoint di progetto. Ad esempio, è possibile determinare se esistono già file nell'elemento di progetto corrente nel percorso di distribuzione e quindi eliminare i file distribuiti prima della distribuzione dell'elemento di progetto corrente. Per altre informazioni sui conflitti di distribuzione, vedere [Estensione SharePoint creazione di pacchetti e distribuzione.](../sharepoint/extending-sharepoint-packaging-and-deployment.md)

### <a name="to-handle-a-deployment-conflict"></a>Per gestire un conflitto di distribuzione

1. Creare un'estensione dell'elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

    - [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Nell'estensione gestire l'evento di un oggetto (in un'estensione dell'elemento di progetto o di un'estensione di progetto) o di un oggetto (in una definizione di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> nuovo tipo di elemento di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> progetto).

3. Nel gestore eventi determinare se è presente un conflitto tra l'elemento di progetto da distribuire e la soluzione distribuita nel sito di SharePoint, in base ai criteri applicabili allo scenario. È possibile usare la proprietà del parametro degli argomenti dell'evento per analizzare l'elemento di progetto da distribuire ed è possibile analizzare i file nel percorso di distribuzione chiamando un comando SharePoint definito a questo <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> scopo.

     Per molti tipi di conflitti, può essere necessario prima determinare quale passaggio di distribuzione è in esecuzione. A tale scopo, è possibile usare <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> la proprietà del parametro degli argomenti dell'evento. Anche se in genere è opportuno rilevare i conflitti durante il passaggio di distribuzione incorporato, è possibile verificare la presenza di conflitti <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> durante qualsiasi passaggio di distribuzione.

4. Se esiste un conflitto, usare <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> il metodo della proprietà degli argomenti <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> dell'evento per creare un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto . Questo oggetto rappresenta il conflitto di distribuzione. Nella chiamata al <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metodo specificare anche il metodo chiamato per risolvere il conflitto.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato il processo di base per la gestione di un conflitto di distribuzione in un'estensione dell'elemento di progetto per gli elementi di progetto di definizione dell'elenco. Per gestire un conflitto di distribuzione per un tipo diverso di elemento di progetto, passare una stringa diversa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Per altre informazioni, vedere [Estendere SharePoint di progetto.](../sharepoint/extending-sharepoint-project-items.md)

 Per semplicità, il gestore eventi in questo esempio presuppone che esista un conflitto di distribuzione (ovvero aggiunge sempre un nuovo oggetto ) e il metodo restituisce semplicemente true per indicare che il conflitto è stato <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> `Resolve` risolto.  In uno scenario reale, il gestore eventi determina innanzitutto se esiste un conflitto tra un file nell'elemento di progetto corrente e un file nel percorso di distribuzione e quindi aggiunge un oggetto solo se esiste un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> conflitto. Ad esempio, è possibile usare la proprietà nel gestore eventi per analizzare i file nell'elemento di progetto e chiamare un comando SharePoint per analizzare i file nel percorso `e.ProjectItem.Files` di distribuzione. Analogamente, in uno scenario reale il metodo potrebbe chiamare un comando SharePoint per risolvere il conflitto `Resolve` nel SharePoint sito. Per altre informazioni sulla creazione di SharePoint, vedere [Procedura: Creare un comando SharePoint comando](../sharepoint/how-to-create-a-sharepoint-command.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si vuole distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere la SharePoint creazione di pacchetti e la distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura: Eseguire il codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Procedura: Creare un comando SharePoint comando](../sharepoint/how-to-create-a-sharepoint-command.md)
