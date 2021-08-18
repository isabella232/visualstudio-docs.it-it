---
title: "Procedura: Aggiungere una proprietà a un'estensione SharePoint Project elemento | Microsoft Docs"
titleSuffix: ''
description: Usare un SharePoint di elemento di progetto per aggiungere una proprietà a qualsiasi SharePoint di progetto già installato in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 482e0e3a797f0906792868a022bea4f7e5aa329e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136131"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Procedura: Aggiungere una proprietà a un'estensione SharePoint elemento di progetto
  È possibile usare un'estensione dell'elemento di progetto per aggiungere una proprietà a qualsiasi SharePoint di progetto già installato in Visual Studio. La proprietà viene visualizzata nella **finestra Proprietà** quando l'elemento di progetto viene selezionato in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stata creata un'estensione dell'elemento di progetto. Per altre informazioni, vedere [Procedura: Creare un'estensione](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)SharePoint Project elemento .

### <a name="to-add-a-property-to-a-project-item-extension"></a>Per aggiungere una proprietà a un'estensione di elemento di progetto

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere a un tipo di elemento di progetto. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.

2. Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> dell'implementazione gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> l'evento del *parametro projectItemType.*

3. Nel gestore eventi per <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> l'evento aggiungere un'istanza della classe properties alla raccolta del parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> dell'evento.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come aggiungere una proprietà denominata **Example Property** all'elemento di progetto Event Receiver.

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs" id="Snippet8":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb" id="Snippet8":::

### <a name="understand-the-code"></a>Informazioni sul codice
 Per assicurarsi che la stessa istanza della classe sia utilizzata ogni volta che si verifica l'evento , l'esempio di codice aggiunge l'oggetto proprietà alla proprietà dell'elemento di progetto la prima volta che si `CustomProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> verifica questo <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> evento. Il codice recupera questo oggetto ogni volta che si verifica di nuovo questo evento. Per altre informazioni sull'uso della proprietà per associare i dati agli elementi di progetto, vedere Associare dati personalizzati SharePoint <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [estensioni degli strumenti.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

 Per rendere persistenti le modifiche al valore della proprietà, la funzione di accesso **set** per salva il nuovo valore nella proprietà dell'oggetto a cui `ExampleProperty` è <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> associata la proprietà. Per altre informazioni sull'uso della proprietà per rendere persistenti i dati con gli elementi di progetto, vedere Salvare i dati nelle estensioni del sistema SharePoint <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> [progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire l'aspetto e il  comportamento di una proprietà personalizzata nella finestra Proprietà applicando gli attributi dello spazio dei <xref:System.ComponentModel> nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: specifica il nome della proprietà visualizzata nella **finestra** Proprietà.

- <xref:System.ComponentModel.DescriptionAttribute>: specifica la stringa di descrizione visualizzata nella parte inferiore **della** finestra Proprietà quando viene selezionata la proprietà .

- <xref:System.ComponentModel.DefaultValueAttribute>: specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: specifica una conversione personalizzata tra la  stringa visualizzata nella finestra Proprietà e un valore di proprietà non stringa.

- <xref:System.ComponentModel.EditorAttribute>: specifica un editor personalizzato da utilizzare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questi esempi richiedono un progetto di libreria di classi con riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida a un'estensione SharePoint elemento di progetto](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
