---
title: "Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint | Microsoft Docs"
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 337536d2219ce8494f96769bc79f10967883e61a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015988"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint
  È possibile utilizzare un'estensione di elemento di progetto per aggiungere una proprietà a qualsiasi elemento del progetto SharePoint già installato in Visual Studio. La proprietà viene visualizzata nella finestra **Proprietà** quando l'elemento del progetto è selezionato in **Esplora soluzioni**.

 Nei passaggi seguenti si presuppone che sia già stata creata un'estensione di elemento di progetto. Per altre informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Per aggiungere una proprietà a un'estensione di elemento di progetto

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere a un tipo di elemento di progetto. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.

2. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del parametro *projectItemType* .

3. Nel gestore eventi per l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, aggiungere un'istanza della classe Properties alla <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro degli argomenti dell'evento.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere una proprietà denominata **example** all'elemento del progetto ricevitore di eventi.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Informazioni sul codice
 Per assicurarsi che venga utilizzata la stessa istanza della `CustomProperties` classe ogni volta che <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> si verifica l'evento, l'esempio di codice aggiunge l'oggetto Properties alla <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell'elemento del progetto la prima volta che si verifica questo evento. Il codice recupera questo oggetto ogni volta che l'evento si verifica di nuovo. Per ulteriori informazioni sull'utilizzo della <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per associare i dati agli elementi del progetto, vedere [associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Per salvare in modo permanente le modifiche apportate al valore della proprietà, la funzione di accesso **set** per `ExampleProperty` Salva il nuovo valore nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto a cui è associata la proprietà. Per ulteriori informazioni sull'utilizzo della <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per salvare in modo permanente i dati con gli elementi del progetto, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire il modo in cui una proprietà personalizzata viene visualizzata e si comporta nella finestra **Proprietà** applicando gli attributi dello <xref:System.ComponentModel> spazio dei nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che viene visualizzata nella finestra **Proprietà** .

- <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione visualizzata nella parte inferiore della finestra **Proprietà** quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa visualizzata nella finestra **Proprietà** e un valore di proprietà non stringa.

- <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da usare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questi esempi richiedono un progetto di libreria di classi con riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: aggiungere una voce di menu di scelta rapida a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Estendi elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
