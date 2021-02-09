---
title: Associazione di dati personalizzati con le estensioni degli strumenti di SharePoint | Microsoft Docs
description: Associare dati personalizzati alle estensioni degli strumenti di SharePoint. Vedere un elenco di oggetti che possono contenere dati personalizzati. Aggiungere e recuperare dati personalizzati.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1b4722f04ae46f85d7cc70dadf6127330e8f6616
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851716"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Associare dati personalizzati alle estensioni degli strumenti di SharePoint
  È possibile aggiungere dati personalizzati a determinati oggetti nelle estensioni degli strumenti di SharePoint. Questa operazione è utile quando si dispone di dati in una parte dell'estensione a cui si desidera accedere in seguito da altro codice nell'estensione. Anziché implementare una modalità personalizzata per archiviare e accedere ai dati, è possibile associare i dati a un oggetto nell'estensione e quindi recuperare i dati dallo stesso oggetto in un secondo momento.

 L'aggiunta di dati personalizzati a oggetti è utile anche quando si desidera mantenere i dati rilevanti per un elemento specifico in Visual Studio. Le estensioni degli strumenti di SharePoint vengono caricate una sola volta in Visual Studio, pertanto l'estensione potrebbe funzionare con diversi elementi, ad esempio progetti, elementi di progetto o nodi di **Esplora server** , in qualsiasi momento. Se si dispone di dati personalizzati rilevanti solo per un elemento specifico, è possibile aggiungere i dati all'oggetto che rappresenta tale elemento.

 Quando si aggiungono dati personalizzati agli oggetti nelle estensioni degli strumenti di SharePoint, i dati non vengono mantenuti. I dati sono disponibili solo durante il ciclo di vita dell'oggetto. Dopo che l'oggetto è stato recuperato da Garbage Collection, i dati andranno perduti.

 Nelle estensioni del sistema di progetto SharePoint, è anche possibile salvare i dati di stringa che vengono mantenuti dopo lo scaricamento di un'estensione. Per ulteriori informazioni, vedere [salvataggio dei dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Oggetti che possono contenere dati personalizzati
 È possibile aggiungere dati personalizzati a qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa l' <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaccia. Questa interfaccia definisce solo una proprietà, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> , che è una raccolta di oggetti dati personalizzati. I tipi seguenti implementano <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Aggiungere e recuperare dati personalizzati
 Per aggiungere dati personalizzati a un oggetto in un'estensione degli strumenti di SharePoint, ottenere la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'oggetto a cui si desidera aggiungere i dati, quindi utilizzare il <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodo per aggiungere i dati all'oggetto.

 Per recuperare dati personalizzati da un oggetto in un'estensione degli strumenti di SharePoint, ottenere la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'oggetto e quindi usare uno dei metodi seguenti:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Questo metodo restituisce **true** se l'oggetto dati esiste oppure **false** se non esiste. È possibile utilizzare questo metodo per recuperare istanze di tipi di valore o tipi di riferimento.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Questo metodo restituisce l'oggetto dati se viene chiuso o **null** se non esiste. È possibile usare questo metodo solo per recuperare le istanze dei tipi di riferimento.

  Nell'esempio di codice seguente viene determinato se un determinato oggetto dati è già associato a un elemento di progetto. Se l'oggetto dati non è già associato all'elemento del progetto, il codice aggiunge l'oggetto alla <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'elemento di progetto. Per vedere questo esempio nel contesto di un esempio più ampio, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>Vedi anche
- [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Procedura dettagliata: creazione di un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: estensione Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
