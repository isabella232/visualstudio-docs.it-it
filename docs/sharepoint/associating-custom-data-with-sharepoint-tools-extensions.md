---
title: Estensioni degli strumenti di associazione di dati personalizzati con SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c4e3cba7d4b05de4d32f31bd39c0e462174695fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951040"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Associare dati personalizzati con le estensioni degli strumenti di SharePoint
  È possibile aggiungere dati personalizzati a determinati oggetti nelle estensioni di strumenti di SharePoint. Ciò è utile quando sono presenti dati in una parte dell'estensione che si desidera accedere in seguito da altro codice nella propria estensione. Anziché implementare un modo personalizzato per archiviare e accedere ai dati, è possibile associare i dati a un oggetto nella propria estensione e quindi recuperare i dati dallo stesso oggetto in un secondo momento.  
  
 Aggiunta di dati personalizzate a oggetti è utile anche quando si desidera mantenere i dati relativi a un elemento specifico in Visual Studio. Le estensioni degli strumenti di SharePoint vengono caricate solo una volta in Visual Studio, pertanto, l'estensione potrebbe funzionare con diversi elementi diversi (ad esempio progetti, gli elementi, del progetto oppure **Esplora Server** nodi) in qualsiasi momento. Se si dispone di dati personalizzate che sono rilevanti solo per un elemento specifico, è possibile aggiungere i dati per l'oggetto che rappresenta tale elemento.  
  
 Quando si aggiungono dati personalizzati agli oggetti nelle estensioni di strumenti di SharePoint, i dati non viene mantenuta. I dati sono disponibili solo durante il ciclo di vita dell'oggetto. Dopo che l'oggetto venga recuperato da garbage collection, i dati vanno persi.  
  
 Nelle estensioni del sistema del progetto SharePoint, è anche possibile salvare i dati di tipo stringa che persiste dopo l'estensione viene scaricata. Per altre informazioni, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Oggetti che possono contenere dati personalizzati
 È possibile aggiungere dati personalizzati a qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaccia. Questa interfaccia definisce solo una delle proprietà, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, che è una raccolta di oggetti dati personalizzati. I tipi seguenti implementano <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="add-and-retrieve-custom-data"></a>Aggiungere e recuperare i dati personalizzati
 Per aggiungere dati personalizzati a un oggetto in un'estensione degli strumenti di SharePoint, ottenere il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'oggetto a cui si desidera aggiungere i dati e quindi usare il <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodo per aggiungere i dati all'oggetto.  
  
 Per recuperare i dati personalizzati da un oggetto in un'estensione degli strumenti di SharePoint, ottenere il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'oggetto e quindi usare uno dei metodi seguenti:  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Questo metodo restituisce **true** se l'oggetto dati è presente, o **false** se non esiste. È possibile utilizzare questo metodo per recuperare le istanze di tipi di valore o i tipi di riferimento.  
  
- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Questo metodo restituisce i dati oggetto, se presente, oppure **null** se non esiste. È possibile utilizzare questo metodo solo per recuperare le istanze dei tipi di riferimento.  
  
  Esempio di codice seguente determina se un determinato oggetto dati è già associato a un elemento del progetto. Se l'oggetto dati non è già associato con l'elemento del progetto, quindi il codice aggiunge l'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'elemento del progetto. Per questo esempio nel contesto di un esempio più esaustivo, vedere [come: Aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Vedere anche
 [Concetti di programmazione e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Procedura dettagliata: Creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Procedura dettagliata: Estensione di Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Procedura: Aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Procedura: Aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
