---
title: 'Procedura: Recuperare il SharePoint Project service | Microsoft Docs'
description: Informazioni su come accedere al SharePoint servizio di progetto estensioni del sistema del progetto, Esplora server o altre estensioni Visual Studio progetto.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: aa962e3b82ec994cfceee3d82566029c536af283
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047621"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Procedura: Recuperare il SharePoint servizio di progetto
  È possibile accedere al SharePoint servizio di progetto nei tipi di soluzioni seguenti:

- Estensione del sistema di SharePoint progetto, ad esempio un'estensione di progetto, un'estensione di elemento di progetto o una definizione del tipo di elemento di progetto. Per altre informazioni su questi tipi di estensioni, vedere [Estendere il SharePoint di progetto](../sharepoint/extending-the-sharepoint-project-system.md).

- Estensione del nodo **SharePoint connessioni** in **Esplora server**. Per altre informazioni su questi tipi di estensioni, vedere Estendere il nodo SharePoint [connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Un altro tipo di Visual Studio estensione, ad esempio un vspackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Recuperare il servizio nelle estensioni del sistema del progetto
 In qualsiasi estensione del SharePoint di progetto, è possibile accedere al servizio di progetto usando la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> proprietà di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> .

 È anche possibile recuperare il servizio di progetto usando le procedure seguenti.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Per recuperare il servizio in un'estensione di progetto

1. Nell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> dell'interfaccia individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo .

2. Usare il *parametro projectService* per accedere al servizio.

     Nell'esempio di codice seguente viene illustrato come usare il servizio di progetto per scrivere un messaggio nella finestra **Output** e nella finestra Elenco **errori** in una semplice estensione di progetto.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Per altre informazioni sulla creazione di estensioni di progetto, vedere [Procedura: Creare un'SharePoint di progetto .](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Per recuperare il servizio in un'estensione di elemento di progetto

1. Nell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> dell'interfaccia individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo .

2. Usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> proprietà del *parametro projectItemType* per recuperare il servizio.

     L'esempio di codice seguente illustra come usare il servizio di progetto per  scrivere un messaggio nella finestra **Output** e nella finestra Elenco errori in una semplice estensione dell'elemento di progetto **Definizione** elenco.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet2":::

     Per altre informazioni sulla creazione di estensioni di elementi di progetto, vedere [Procedura: Creare un'estensione](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)SharePoint elemento di progetto .

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Per recuperare il servizio in una definizione del tipo di elemento di progetto

1. Nell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> dell'interfaccia individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo .

2. Usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> proprietà del *parametro typeDefinition* per recuperare il servizio.

     L'esempio di codice seguente illustra come usare il servizio di progetto per  scrivere un messaggio nella finestra **Output** e nella finestra Elenco errori in una semplice definizione del tipo di elemento di progetto.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs" id="Snippet3":::

     Per altre informazioni sulla definizione dei tipi di elemento di progetto, vedere [Procedura: Definire un SharePoint tipo di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Recuperare il servizio nelle estensioni Esplora server
 In un'estensione **del nodo SharePoint connections** in **Esplora server** è possibile accedere al servizio di progetto usando la proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> .

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Per recuperare il servizio in un'estensione Esplora server

1. Ottenere un <xref:System.IServiceProvider> oggetto dalla proprietà di un oggetto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> nell'estensione.

2. Usare il <xref:System.IServiceProvider.GetService%2A> metodo per richiedere un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> .

     Nell'esempio di codice seguente viene illustrato come usare il servizio di progetto  per scrivere un messaggio nella finestra **Output** e nella finestra Elenco errori da un menu di scelta rapida aggiunto dall'estensione ai nodi dell'elenco **Esplora server**.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs" id="Snippet1":::

     Per altre informazioni sull'estensione **del nodo SharePoint Connections** in **Esplora server**, vedere [Procedura:](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)Estendere un nodo SharePoint in Esplora server .

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Recuperare il servizio in altre estensioni Visual Studio
 È possibile recuperare il servizio di progetto in un pacchetto VSPackage o in qualsiasi estensione Visual Studio che abbia accesso a un oggetto nel modello a oggetti di automazione, ad esempio una procedura guidata del modello di progetto che implementa l'interfaccia <xref:EnvDTE80.DTE2> <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> .

 In un VSPackage è possibile richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto usando uno dei metodi seguenti:

- Metodo <xref:System.IServiceProvider.GetService%2A> di un VSPackage gestito che deriva dalla <xref:Microsoft.VisualStudio.Shell.Package> classe . Per altre informazioni, vedere [Procedura: Ottenere un servizio](../extensibility/how-to-get-a-service.md).

- Metodo <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> statico. Per altre informazioni, vedere [Usare GetGlobalService.](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice)

  In un Visual Studio che ha accesso a un oggetto , è possibile richiedere un oggetto <xref:EnvDTE80.DTE2> usando il metodo di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> <xref:Microsoft.VisualStudio.Shell.ServiceProvider> . Per altre informazioni, vedere [Recupero di un servizio dall'oggetto DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Vedi anche
- [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md)
- [Procedura: Ottenere un servizio](../extensibility/how-to-get-a-service.md)
- [Procedura: Usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)
