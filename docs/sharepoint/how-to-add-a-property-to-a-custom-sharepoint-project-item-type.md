---
title: 'Procedura: Aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e9695755967aa1b66aa7cda2d784ae88b0fc1b42
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104408"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Procedura: Aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una proprietà all'elemento del progetto. La proprietà viene visualizzata nel **delle proprietà** finestra quando l'elemento del progetto viene selezionato in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stata definita il proprio tipo di elemento di progetto SharePoint. Per altre informazioni, vedere [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Per aggiungere una proprietà a una definizione di un tipo di elemento di progetto

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà a cui che si sta aggiungendo al tipo di elemento di progetto personalizzato. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto personalizzati, è possibile definire tutte le proprietà della stessa classe o in diverse classi.

2. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo delle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del *projectItemTypeDefinition* parametro.

3. Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà personalizzate per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro di argomenti dell'evento.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come aggiungere una proprietà denominata **esempio di proprietà** su un oggetto personalizzato elemento di progetto tipo.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Informazioni sul codice
 Per garantire che la stessa istanza del `CustomProperties` classe viene utilizzata ogni volta che il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento si verifica, l'esempio di codice consente di salvare l'oggetto delle proprietà per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà di questo evento si verifica il tempo di elemento al primo progetto. Il codice recupera l'oggetto ogni volta che questo evento viene generato nuovamente. Per altre informazioni sull'uso di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per salvare i dati con elementi di progetto, vedere [estensioni degli strumenti di associazione dati personalizzati con SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Per rendere persistenti le modifiche apportate al valore della proprietà, il **impostata** funzione di accesso per `ExampleProperty` Salva il nuovo valore per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto che è associata la proprietà. Per altre informazioni sull'uso di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per rendere persistenti i dati con elementi di progetto, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire come una proprietà personalizzata viene visualizzata e si comporta come la **delle proprietà** finestra applicando gli attributi dal <xref:System.ComponentModel> dello spazio dei nomi per la definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che viene visualizzato nei **proprietà** finestra.

- <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione che viene visualizzato in fondo il **proprietà** finestra quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa che viene visualizzata nei **proprietà** finestra e un valore della proprietà non di tipo stringa.

- <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da utilizzare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questi esempi di codice è necessario un progetto libreria di classi con i riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento del progetto
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Per distribuire l'elemento del progetto, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly, il modello e qualsiasi altro file che si desidera distribuire con l'elemento del progetto. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definizione di tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
