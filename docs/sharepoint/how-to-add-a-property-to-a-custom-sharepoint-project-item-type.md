---
title: Aggiungere la proprietà al tipo di elemento di progetto SharePoint personalizzato
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 54765b9b6b82214a7deccaee4f9ee671a72dd40d
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016004"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una proprietà all'elemento del progetto. La proprietà viene visualizzata nella finestra **Proprietà** quando l'elemento del progetto è selezionato in **Esplora soluzioni**.

 Nei passaggi seguenti si presuppone che sia già stato definito un tipo di elemento di progetto SharePoint personalizzato. Per altre informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Per aggiungere una proprietà a una definizione di un tipo di elemento di progetto

1. Definire una classe con una proprietà pubblica che rappresenti la proprietà che si sta aggiungendo al tipo di elemento di progetto personalizzato. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto personalizzato, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.

2. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del parametro *ProjectItemTypeDefinition* .

3. Nel gestore eventi per l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà personalizzata alla <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro degli argomenti dell'evento.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere una proprietà di **esempio denominata Property** a un tipo di elemento di progetto personalizzato.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Informazioni sul codice
 Per assicurarsi che venga utilizzata la stessa istanza della `CustomProperties` classe ogni volta <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> che si verifica l'evento, l'esempio di codice salva l'oggetto proprietà nella <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'elemento del progetto la prima volta che si verifica questo evento. Il codice recupera questo oggetto ogni volta che l'evento si verifica di nuovo. Per altre informazioni sull'uso della <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per salvare i dati con gli elementi del progetto, vedere [associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Per salvare in modo permanente le modifiche apportate al valore della proprietà, la funzione di accesso **set** per `ExampleProperty` Salva il nuovo valore nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto a cui è associata la proprietà. Per ulteriori informazioni sull'utilizzo della <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per salvare in modo permanente i dati con gli elementi del progetto, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire il modo in cui una proprietà personalizzata viene visualizzata e si comporta nella finestra **Proprietà** applicando gli attributi dello <xref:System.ComponentModel> spazio dei nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che viene visualizzata nella finestra **Proprietà** .

- <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione visualizzata nella parte inferiore della finestra **Proprietà** quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa visualizzata nella finestra **Proprietà** e un valore di proprietà non stringa.

- <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da usare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questi esempi di codice richiedono un progetto di libreria di classi con riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento di progetto
 Per consentire ad altri sviluppatori di usare l'elemento del progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Per distribuire l'elemento di progetto, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly, il modello e qualsiasi altro file che si vuole distribuire con l'elemento del progetto. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definizione di tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
