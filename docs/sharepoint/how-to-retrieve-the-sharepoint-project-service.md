---
title: 'Procedura: recuperare il servizio di progetto SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e2dc633621734740065b8e0c80dd34795eac830
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119911"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Procedura: recuperare il servizio di progetto SharePoint
  È possibile accedere al servizio di progetto SharePoint nei seguenti tipi di soluzioni:  
  
-   Estensione del sistema del progetto SharePoint, ad esempio un'estensione di progetto, estensione di elemento di progetto o definizione di tipo di elemento di progetto. Per altre informazioni su questi tipi di estensioni, vedere [estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Un'estensione del **connessioni di SharePoint** nodo **Esplora Server**. Per altre informazioni su questi tipi di estensioni, vedere [estendere del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Un altro tipo di estensione di Visual Studio, ad esempio un pacchetto VSPackage.  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>Recuperare il servizio nelle estensioni di sistema di progetto  
 In qualsiasi estensione del sistema del progetto SharePoint, è possibile accedere al servizio di progetto utilizzando il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto.  
  
 È inoltre possibile recuperare il servizio di progetto utilizzando le procedure seguenti.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Per recuperare il servizio in un'estensione di progetto  
  
1.  Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'interfaccia, individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> (metodo).  
  
2.  Usare la *projectService* parametro per accedere al servizio.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto per scrivere un messaggio per il **Output** finestra e **elenco errori** in un'estensione di progetto semplice.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Per altre informazioni sulla creazione di estensioni di progetto, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Per recuperare il servizio in un'estensione di elemento di progetto  
  
1.  Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> l'interfaccia, individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> (metodo).  
  
2.  Usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> proprietà del *projectItemType* parametro per recuperare il servizio.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto per scrivere un messaggio per il **Output** finestra e **elenco errori** finestra in una semplice estensione del **definizione elenco** elemento del progetto.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Per altre informazioni sulla creazione di estensioni dell'elemento del progetto, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Per recuperare il servizio in una definizione di tipo di elemento di progetto  
  
1.  Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'interfaccia, individuare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (metodo).  
  
2.  Usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> proprietà del *typeDefinition* parametri per recuperare il servizio.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto per scrivere un messaggio per il **Output** finestra e **elenco errori** finestra in una definizione di tipo di elemento di progetto semplice.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Per altre informazioni sulla definizione dei tipi di elemento di progetto, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Recuperare il servizio nelle estensioni di Esplora Server  
 In un'estensione del **connessioni di SharePoint** nodo **Esplora Server**, è possibile accedere al servizio di progetto utilizzando il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Per recuperare il servizio in un'estensione di Esplora Server  
  
1.  Ottenere un <xref:System.IServiceProvider> dall'oggetto di <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto nella propria estensione.  
  
2.  Usare la <xref:System.IServiceProvider.GetService%2A> metodo per richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto.  
  
     Esempio di codice seguente viene illustrato come utilizzare il servizio di progetto per scrivere un messaggio per il **Output** finestra e **elenco errori** finestra dal menu di scelta rapida che consente di aggiungere l'estensione per i nodi elenco **Esplora server**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Per altre informazioni sull'estensione il **connessioni di SharePoint** nodo **Esplora Server**, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Recuperare il servizio in altre estensioni di Visual Studio  
 È possibile recuperare il servizio del progetto in un pacchetto VSPackage o in qualsiasi estensione di Visual Studio che può accedere a un <xref:EnvDTE80.DTE2> oggetti nel modello a oggetti di automazione, ad esempio la creazione guidata modello di progetto che implementa il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia.  
  
 In un pacchetto VSPackage, è possibile richiedere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto usando uno dei metodi seguenti:  
  
-   Il <xref:System.IServiceProvider.GetService%2A> metodo di un pacchetto VSPackage gestito da cui deriva il <xref:Microsoft.VisualStudio.Shell.Package> classe. Per altre informazioni, vedere [procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md).  
  
-   Il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> (metodo). Per altre informazioni, vedere [usare GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
 In un'estensione di Visual Studio che può accedere a un <xref:EnvDTE80.DTE2> oggetto, è possibile richiedere un' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto tramite il <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodo di un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> oggetto. Per altre informazioni, vedere [recupero di un servizio dall'oggetto DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Vedere anche
 [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Procedura: ottenere un servizio](../extensibility/how-to-get-a-service.md)   
 [Procedura: usare procedure guidate con modelli di progetto](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
