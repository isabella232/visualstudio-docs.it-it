---
title: 'Procedura: eseguire codice quando vengono eseguiti i passaggi di distribuzione | Microsoft Docs'
description: Eseguire il codice per gestire gli eventi generati dagli elementi del progetto SharePoint prima e dopo l'esecuzione di una fase di distribuzione da Visual Studio.
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
ms.openlocfilehash: 0b3037c0ec983b9f496947feba41938111fafc38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851582"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Procedura: eseguire codice quando vengono eseguiti i passaggi di distribuzione
  Se si desidera eseguire attività aggiuntive per un passaggio di distribuzione in un progetto SharePoint, è possibile gestire gli eventi generati dagli elementi del progetto SharePoint prima e dopo l'esecuzione di ogni passaggio di distribuzione da Visual Studio. Per ulteriori informazioni, vedere [estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Per eseguire il codice quando vengono eseguiti i passaggi di distribuzione

1. Creare un'estensione di elemento del progetto, un'estensione di progetto o una definizione di un nuovo tipo di elemento di progetto. Per altre informazioni, vedere i seguenti argomenti:

    - [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Nell'estensione, gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> eventi e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto (in un'estensione di elemento di progetto o di progetto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto (in una definizione di un nuovo tipo di elemento di progetto).

3. Nei gestori eventi usare i <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parametri e per ottenere informazioni sul passaggio di distribuzione. Ad esempio, è possibile determinare quale passaggio di distribuzione è in esecuzione e se la soluzione viene distribuita o ritratta.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come gestire gli <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventi e in un'estensione per l'elemento di progetto dell'istanza dell'elenco. Questa estensione scrive un messaggio aggiuntivo nella finestra di **output** quando Visual Studio ricicla il pool di applicazioni durante la distribuzione e la ritrazione della soluzione.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estensione della creazione di pacchetti e della distribuzione di SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Procedura dettagliata: creare un passaggio di distribuzione personalizzato per i progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Procedura: eseguire codice quando un progetto SharePoint viene distribuito o ritratto](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
