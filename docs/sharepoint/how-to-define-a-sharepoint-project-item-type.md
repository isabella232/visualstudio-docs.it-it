---
title: 'Procedura: definire un tipo di elemento di progetto SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3e35087481e1cdb536fddb4181f251e5595b365c
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119932"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Procedura: definire un tipo di elemento di progetto SharePoint
  Definire un tipo di elemento di progetto quando si desidera creare un elemento di progetto SharePoint personalizzato. Per altre informazioni, vedere [definizione di tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Per definire un tipo di elemento di progetto  
  
1.  Creare un progetto Libreria di classi.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Aggiungere gli attributi seguenti alla classe:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo al costruttore dell'attributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In una definizione di tipo elemento di progetto, questo attributo specifica l'identificatore di stringa per il nuovo elemento di progetto. Si consiglia di utilizzare il formato *nome società*. *nome della funzionalità* per assicurarsi che tutti gli elementi di progetto hanno un nome univoco.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Questo attributo specifica l'icona da visualizzare per questo elemento del progetto in **Esplora soluzioni**. Questo attributo è facoltativo. Se non si applica alla classe, Visual Studio visualizza un'icona predefinita per l'elemento del progetto. Se si imposta questo attributo, passare il nome completo di un'icona o bitmap incorporata nell'assembly.  
  
5.  Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo, utilizzare i membri del *projectItemTypeDefinition* parametro per definire il comportamento del tipo di elemento di progetto. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto che fornisce accesso agli eventi definiti nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfacce. Per accedere a un'istanza specifica del tipo di elemento di progetto, gestiscono <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi, ad esempio <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come definire un tipo di elemento di progetto semplice. Questo tipo di elemento di progetto scrive un messaggio per il **Output** finestra e **elenco errori** finestra quando un utente aggiunge un elemento del progetto di questo tipo a un progetto.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 Questo esempio Usa il servizio di progetto SharePoint in cui per scrivere il messaggio il **Output** finestra e **elenco errori** finestra. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Distribuire l'elemento del progetto  
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Per distribuire l'elemento del progetto, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly, il modello e qualsiasi altro file che si desidera distribuire con l'elemento del progetto. Per altre informazioni, vedere [gli strumenti di distribuzione di estensioni per SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Definire tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creare modelli di elementi e modelli di progetto per elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Procedura dettagliata: Creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
