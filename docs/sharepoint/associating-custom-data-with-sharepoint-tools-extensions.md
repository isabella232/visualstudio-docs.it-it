---
title: Associazione di dati personalizzati con SharePoint Tools | Microsoft Docs
description: Associare dati personalizzati alle estensioni SharePoint tools. Vedere un elenco di oggetti che possono contenere dati personalizzati. Aggiungere e recuperare dati personalizzati.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dcd6e00fa9a934a159b49aec225813cec92b08ec11076d29716c30e38e76a891
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315343"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Associare dati personalizzati alle estensioni SharePoint strumenti di configurazione
  È possibile aggiungere dati personalizzati a determinati oggetti nelle estensioni SharePoint strumenti. Ciò è utile quando si dispone di dati in una parte dell'estensione a cui si vuole accedere in un secondo momento da altro codice nell'estensione. Anziché implementare un modo personalizzato per archiviare e accedere ai dati, è possibile associare i dati a un oggetto nell'estensione e quindi recuperare i dati dallo stesso oggetto in un secondo momento.

 L'aggiunta di dati personalizzati agli oggetti è utile anche quando si vogliono mantenere i dati rilevanti per un elemento specifico in Visual Studio. SharePoint le estensioni degli strumenti vengono caricate una sola volta in Visual Studio, quindi l'estensione potrebbe funzionare con diversi elementi diversi (ad esempio progetti, elementi di progetto o nodi Esplora server) **in qualsiasi** momento. Se si dispone di dati personalizzati rilevanti solo per un elemento specifico, è possibile aggiungere i dati all'oggetto che rappresenta tale elemento.

 Quando si aggiungono dati personalizzati agli oggetti nelle estensioni SharePoint tools, i dati non vengono mantenuti. I dati sono disponibili solo durante la durata dell'oggetto . Dopo che l'oggetto è stato recuperato da Garbage Collection, i dati vengono persi.

 Nelle estensioni del sistema SharePoint progetto, è anche possibile salvare i dati stringa che vengono mantenuti dopo lo scaricamento di un'estensione. Per altre informazioni, vedere [Salvataggio di dati nelle estensioni del SharePoint di progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Oggetti che possono contenere dati personalizzati
 È possibile aggiungere dati personalizzati a qualsiasi oggetto nel modello a oggetti SharePoint tools che implementa <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> l'interfaccia . Questa interfaccia definisce una sola proprietà, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> , che è una raccolta di oggetti dati personalizzati. I tipi seguenti implementano <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

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
 Per aggiungere dati personalizzati a un oggetto in un'estensione degli strumenti di SharePoint, ottenere la proprietà dell'oggetto a cui si desidera aggiungere i dati e quindi usare il metodo per aggiungere i dati <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> all'oggetto .

 Per recuperare dati personalizzati da un oggetto in un'estensione SharePoint tools, ottenere la proprietà dell'oggetto e quindi <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> usare uno dei metodi seguenti:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Questo metodo restituisce **true se** l'oggetto dati esiste oppure **false** se non esiste. È possibile usare questo metodo per recuperare istanze di tipi valore o tipi riferimento.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Questo metodo restituisce l'oggetto dati se viene chiuso oppure **null** se non esiste. È possibile usare questo metodo solo per recuperare istanze di tipi riferimento.

  L'esempio di codice seguente determina se un determinato oggetto dati è già associato a un elemento di progetto. Se l'oggetto dati non è già associato all'elemento di progetto, il codice aggiunge l'oggetto <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> alla proprietà dell'elemento di progetto. Per visualizzare questo esempio nel contesto di un esempio più ampio, vedere [Procedura:](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)Aggiungere una proprietà a un elemento SharePoint tipo di elemento di progetto .

  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet13":::
  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet13":::

## <a name="see-also"></a>Vedi anche
- [Concetti e funzionalità di programmazione per SharePoint tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Procedura dettagliata: Creazione di un elemento di progetto di azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: Estensione di Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Procedura: Aggiungere una proprietà ai SharePoint progetto](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
