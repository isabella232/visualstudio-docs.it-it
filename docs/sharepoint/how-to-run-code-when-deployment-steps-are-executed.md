---
title: 'Procedura: Eseguire codice quando vengono eseguiti i passaggi di distribuzione | Microsoft Docs'
description: Eseguire il codice per gestire gli eventi generati da SharePoint di progetto prima e dopo Visual Studio esegue un passaggio di distribuzione.
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
ms.openlocfilehash: 7d23b6d2bfdc3cbf619dcad4e96fc4a577bf8f90ec864292cb7aac2b3a2ebf26
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352890"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Procedura: Eseguire codice quando vengono eseguiti i passaggi di distribuzione
  Se si desidera eseguire attività aggiuntive per un passaggio di distribuzione in un progetto SharePoint, è possibile gestire gli eventi generati dagli elementi del progetto SharePoint prima e dopo che Visual Studio esegue ogni passaggio di distribuzione. Per altre informazioni, vedere [Estensione SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Per eseguire il codice quando vengono eseguiti i passaggi di distribuzione

1. Creare un'estensione di elemento di progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

    - [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Procedura: Definire un tipo di SharePoint di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Nell'estensione gestire gli eventi e di un oggetto (in un'estensione di elemento di progetto o di progetto) o di un oggetto (in una definizione di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> un nuovo tipo di elemento di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> progetto).

3. Nei gestori eventi usare i parametri <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> e per ottenere informazioni sul passaggio di <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> distribuzione. Ad esempio, è possibile determinare quale passaggio di distribuzione è in esecuzione e se la soluzione viene distribuita o ritirata.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> eventi e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> in un'estensione per l'elemento di progetto List Instance. Questa estensione scrive un messaggio aggiuntivo nella finestra **Output** quando Visual Studio ricicla il pool di applicazioni durante la distribuzione e la ritrazione della soluzione.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb" id="Snippet4":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs" id="Snippet4":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint creazione di pacchetti e distribuzione](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per SharePoint progetto](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Procedura: Eseguire codice quando un SharePoint viene distribuito o ritirato](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
