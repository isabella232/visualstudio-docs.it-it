---
title: "Procedura: creare un'estensione di elemento di progetto SharePoint | Microsoft Docs"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 93459096e6d88ce3754c32bf7f61a3cf369cbeba
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119872"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Procedura: creare un'estensione di elemento di progetto SharePoint
  Creare un'estensione di elemento di progetto quando si desidera aggiungere funzionalità a un elemento di progetto SharePoint che è già installato in Visual Studio. Per altre informazioni, vedere [elementi di progetto SharePoint estendere](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>Per creare un'estensione di elemento di progetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Aggiungere gli attributi seguenti alla classe:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> tipo al costruttore dell'attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In un'estensione di elemento di progetto, questo attributo identifica l'elemento del progetto da estendere. Passare l'ID dell'elemento del progetto per il costruttore dell'attributo. Per un elenco di ID degli elementi di progetto che sono inclusi con Visual Studio, vedere [elementi di progetto SharePoint estendere](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo, utilizzare i membri del *projectItemType* parametro per definire il comportamento dell'estensione. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> oggetto che fornisce accesso agli eventi definiti nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfacce. Per accedere a un'istanza specifica del tipo di elemento di progetto si estende, gestiscono <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi, ad esempio <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come creare una semplice estensione per l'elemento di progetto del ricevitore di eventi. Ogni volta che l'utente aggiunge un elemento di progetto del ricevitore di eventi a un progetto SharePoint, tale estensione scrive un messaggio per il **Output** finestra e **elenco errori** finestra.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 Questo esempio Usa il servizio di progetto SharePoint in cui per scrivere il messaggio il **Output** finestra e **elenco errori** finestra. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Distribuire l'estensione  
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Estendere gli elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  
