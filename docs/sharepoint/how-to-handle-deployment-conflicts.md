---
title: 'Procedura: gestire i conflitti di distribuzione | Microsoft Docs'
description: Vedere un esempio di come implementare il proprio codice per gestire i conflitti di distribuzione per un elemento del progetto SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b09db3fecde5d4b87b24963930b2783b0c68052c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213979"
---
# <a name="how-to-handle-deployment-conflicts"></a>Procedura: gestire i conflitti di distribuzione
  È possibile fornire codice personalizzato per gestire i conflitti di distribuzione per un elemento del progetto SharePoint. Ad esempio, è possibile determinare se i file nell'elemento del progetto corrente sono già presenti nel percorso di distribuzione e quindi eliminare i file distribuiti prima della distribuzione dell'elemento del progetto corrente. Per ulteriori informazioni sui conflitti di distribuzione, vedere estensione della creazione [di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Per gestire un conflitto di distribuzione

1. Creare un'estensione di elemento del progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

    - [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Nell'estensione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> evento di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto (in un'estensione di elemento di progetto o di progetto) o in un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto (in una definizione di un nuovo tipo di elemento di progetto).

3. Nel gestore eventi, determinare se esiste un conflitto tra l'elemento del progetto che viene distribuito e la soluzione distribuita nel sito di SharePoint, in base ai criteri applicabili allo scenario. È possibile utilizzare la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> proprietà del parametro argomenti evento per analizzare l'elemento del progetto che viene distribuito ed è possibile analizzare i file nel percorso di distribuzione chiamando un comando di SharePoint definito a questo scopo.

     Per molti tipi di conflitti, potrebbe essere necessario innanzitutto determinare quale passaggio di distribuzione è in esecuzione. A tale scopo, è possibile usare la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> proprietà del parametro degli argomenti dell'evento. Sebbene in genere sia opportuno rilevare i conflitti durante il <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> passaggio di distribuzione predefinito, è possibile verificare la presenza di conflitti durante qualsiasi passaggio di distribuzione.

4. Se esiste un conflitto, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metodo della <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> proprietà degli argomenti dell'evento per creare un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto. Questo oggetto rappresenta il conflitto di distribuzione. Nella chiamata al <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> metodo, specificare anche il metodo chiamato per risolvere il conflitto.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato il processo di base per la gestione di un conflitto di distribuzione in un'estensione di elemento di progetto per gli elementi del progetto di definizione elenco. Per gestire un conflitto di distribuzione per un tipo diverso di elemento di progetto, passare una stringa diversa a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Per altre informazioni, vedere [estendere gli elementi del progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).

 Per semplicità, il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> gestore eventi in questo esempio presuppone che esista un conflitto di distribuzione, ovvero aggiunge sempre un nuovo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto, e il `Resolve` metodo restituisce semplicemente **true** per indicare che il conflitto è stato risolto. In uno scenario reale, il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> gestore eventi determina innanzitutto se esiste un conflitto tra un file nell'elemento di progetto corrente e un file nel percorso di distribuzione e quindi aggiunge un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> oggetto solo se esiste un conflitto. Ad esempio, è possibile usare la `e.ProjectItem.Files` proprietà nel gestore eventi per analizzare i file nell'elemento del progetto ed è possibile chiamare un comando di SharePoint per analizzare i file nel percorso di distribuzione. Analogamente, in uno scenario reale il `Resolve` metodo può chiamare un comando di SharePoint per risolvere il conflitto nel sito di SharePoint. Per ulteriori informazioni sulla creazione di comandi di SharePoint, vedere [procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estendi elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura: eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
