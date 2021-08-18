---
title: Aggiungere una proprietà al tipo di elemento SharePoint progetto personalizzato
description: Aggiungere una proprietà a un tipo di elemento SharePoint progetto personalizzato. La proprietà viene visualizzata nel Finestra Proprietà quando l'elemento di progetto viene selezionato in Esplora soluzioni.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: cde438dc6a43f158d119ac380a28bd276c04c7e1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149091"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Procedura: Aggiungere una proprietà a un tipo di elemento SharePoint progetto personalizzato
  Quando si definisce un tipo di SharePoint progetto personalizzato, è possibile aggiungere una proprietà all'elemento di progetto. La proprietà viene visualizzata nella **finestra Proprietà** quando l'elemento di progetto viene selezionato in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stato definito il proprio SharePoint tipo di elemento di progetto. Per altre informazioni, vedere [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Per aggiungere una proprietà a una definizione di un tipo di elemento di progetto

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere al tipo di elemento di progetto personalizzato. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto personalizzato, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.

2. Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> dell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> l'evento del *parametro projectItemTypeDefinition.*

3. Nel gestore eventi per <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> l'evento aggiungere un'istanza della classe di proprietà personalizzate alla raccolta del parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> dell'evento.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come aggiungere una proprietà denominata **Example Property** a un tipo di elemento di progetto personalizzato.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet11":::

### <a name="understand-the-code"></a>Informazioni sul codice
 Per assicurarsi che la stessa istanza della classe sia utilizzata ogni volta che si verifica l'evento, l'esempio di codice salva l'oggetto proprietà nella proprietà dell'elemento di progetto la prima volta che si verifica questo `CustomProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> evento. Il codice recupera questo oggetto ogni volta che si verifica nuovamente questo evento. Per altre informazioni sull'uso della proprietà per salvare i dati con gli elementi di progetto, vedere Associare dati personalizzati <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [alle estensioni SharePoint tools.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

 Per rendere persistenti le modifiche al valore della proprietà, la funzione di accesso **set** per salva il nuovo valore nella proprietà dell'oggetto a cui `ExampleProperty` è <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> associata la proprietà. Per altre informazioni sull'uso della proprietà per rendere persistenti i dati con gli elementi di progetto, vedere Salvare i dati nelle estensioni <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> del sistema SharePoint progetto [.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire l'aspetto e il  comportamento di una proprietà personalizzata nella finestra Proprietà applicando gli attributi dello spazio dei <xref:System.ComponentModel> nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: specifica il nome della proprietà visualizzata nella **finestra** Proprietà.

- <xref:System.ComponentModel.DescriptionAttribute>: specifica la stringa di descrizione visualizzata nella parte inferiore **della** finestra Proprietà quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: specifica una conversione personalizzata tra la  stringa visualizzata nella finestra Proprietà e un valore della proprietà non stringa.

- <xref:System.ComponentModel.EditorAttribute>: specifica un editor personalizzato da usare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questi esempi di codice richiedono un progetto libreria di classi con riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento di progetto
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [Creare modelli di elemento e modelli di progetto per SharePoint di progetto.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 Per distribuire l'elemento di progetto, creare un pacchetto di estensione (VSIX) per l'assembly, il modello e qualsiasi altro file da distribuire con [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] l'elemento di progetto. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definizione di tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
