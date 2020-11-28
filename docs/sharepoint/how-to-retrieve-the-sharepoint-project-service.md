---
title: 'Procedura: recuperare il servizio di progetto SharePoint | Microsoft Docs'
description: Informazioni su come accedere al servizio di progetto SharePoint nelle estensioni del sistema di progetto, Esplora server estensioni o altre estensioni di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 553b4ae3b7ecfa9fa49065824020ebdcecf77215
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304441"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Procedura: recuperare il servizio di progetto SharePoint
  È possibile accedere al servizio di progetto SharePoint nei seguenti tipi di soluzioni:

- Estensione del sistema del progetto SharePoint, ad esempio un'estensione di progetto, un'estensione di elemento di progetto o una definizione del tipo di elemento di progetto. Per ulteriori informazioni su questi tipi di estensioni, vedere [estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Estensione del nodo **connessioni di SharePoint** in **Esplora server**. Per ulteriori informazioni su questi tipi di estensioni, vedere [estensione del nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Un altro tipo di estensione di Visual Studio, ad esempio un pacchetto VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Recuperare il servizio nelle estensioni del sistema di progetto
 In qualsiasi estensione del sistema del progetto SharePoint, è possibile accedere al servizio del progetto utilizzando la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto.

 È inoltre possibile recuperare il servizio del progetto utilizzando le procedure seguenti.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Per recuperare il servizio in un'estensione di progetto

1. Nell'implementazione dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaccia individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo.

2. Usare il parametro *ProjectService* per accedere al servizio.

     Nell'esempio di codice seguente viene illustrato come utilizzare il servizio del progetto per scrivere un messaggio nella finestra di **output** e **Elenco errori** finestra in una semplice estensione di progetto.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Per ulteriori informazioni sulla creazione di estensioni di progetto, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Per recuperare il servizio in un'estensione di elemento del progetto

1. Nell'implementazione dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaccia individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo.

2. Utilizzare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> proprietà del parametro *projectItemType* per recuperare il servizio.

     Nell'esempio di codice riportato di seguito viene illustrato come utilizzare il servizio del progetto per scrivere un messaggio nella finestra di **output** e **Elenco errori** finestra in una semplice estensione dell'elemento di progetto **definizione elenco** .

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Per ulteriori informazioni sulla creazione di estensioni di elementi di progetto, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Per recuperare il servizio in una definizione di tipo di elemento di progetto

1. Nell'implementazione dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaccia individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo.

2. Utilizzare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> proprietà del parametro *typeDefinition* per recuperare il servizio.

     Nell'esempio di codice seguente viene illustrato come utilizzare il servizio del progetto per scrivere un messaggio nella finestra di **output** e **Elenco errori** finestra in una definizione di tipo di elemento di progetto semplice.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Per ulteriori informazioni sulla definizione dei tipi di elementi di progetto, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Recuperare il servizio in Esplora server Extensions
 In un'estensione del nodo **connessioni di SharePoint** in **Esplora server**, è possibile accedere al servizio del progetto utilizzando la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Per recuperare il servizio in un'estensione Esplora server

1. Ottenere un <xref:System.IServiceProvider> oggetto dalla <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto nell'estensione.

2. Usare il <xref:System.IServiceProvider.GetService%2A> metodo per richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto.

     Nell'esempio di codice riportato di seguito viene illustrato come utilizzare il servizio del progetto per scrivere un messaggio nella finestra di **output** e **Elenco errori** finestra da un menu di scelta rapida aggiunto dall'estensione ai nodi dell'elenco **Esplora server**.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Per ulteriori informazioni sull'estensione del nodo **connessioni di SharePoint** in **Esplora server**, vedere [procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Recuperare il servizio in altre estensioni di Visual Studio
 È possibile recuperare il servizio del progetto in un VSPackage o in qualsiasi estensione di Visual Studio che abbia accesso a un <xref:EnvDTE80.DTE2> oggetto nel modello a oggetti di automazione, ad esempio una procedura guidata per i modelli di progetto che implementa l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.

 In un pacchetto VSPackage è possibile richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto utilizzando uno dei metodi seguenti:

- <xref:System.IServiceProvider.GetService%2A>Metodo di un VSPackage gestito che deriva dalla <xref:Microsoft.VisualStudio.Shell.Package> classe. Per altre informazioni, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md).

- Metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> . Per altre informazioni, vedere [usare GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  In un'estensione di Visual Studio che ha accesso a un <xref:EnvDTE80.DTE2> oggetto, è possibile richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto usando il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo di un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> oggetto. Per ulteriori informazioni, vedere [recupero di un servizio dall'oggetto DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Vedere anche
- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)
- [Procedura: utilizzare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
