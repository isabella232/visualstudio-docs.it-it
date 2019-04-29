---
title: "Procedura: Aggiungere una proprietà a un'estensione di elemento di progetto SharePoint | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 20a7abaa8c132b3cd1679ab95ed8154b8ca86502
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967227"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Procedura: Aggiungere una proprietà a un'estensione di elemento di progetto SharePoint
  È possibile utilizzare un'estensione di elemento di progetto per aggiungere una proprietà in qualsiasi elemento di progetto SharePoint che è già installato in Visual Studio. La proprietà viene visualizzata nel **delle proprietà** finestra quando l'elemento del progetto viene selezionato in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che un'estensione di elemento di progetto è già stato creato. Per altre informazioni, vedere [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Per aggiungere una proprietà a un'estensione di elemento di progetto

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà che si aggiungono a un tipo di elemento di progetto. Se si desidera aggiungere più proprietà a un tipo di elemento di progetto, è possibile definire tutte le proprietà della stessa classe o in diverse classi.

2. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo delle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento del *projectItemType* parametro.

3. Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro di argomenti dell'evento.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come aggiungere una proprietà denominata **esempio di proprietà** all'elemento del progetto ricevitore di eventi.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Informazioni sul codice
 Per garantire che la stessa istanza del `CustomProperties` classe viene utilizzata ogni volta che il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento si verifica, l'esempio di codice aggiunge l'oggetto delle proprietà per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà di questo evento si verifica il tempo di elemento al primo progetto. Il codice recupera l'oggetto ogni volta che questo evento viene generato nuovamente. Per altre informazioni sull'uso di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per associare dati a elementi di progetto, vedere [estensioni degli strumenti di associazione dati personalizzati con SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Per rendere persistenti le modifiche apportate al valore della proprietà, il **impostata** funzione di accesso per `ExampleProperty` Salva il nuovo valore per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto che è associata la proprietà. Per altre informazioni sull'uso di <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per rendere persistenti i dati con elementi di progetto, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire come una proprietà personalizzata viene visualizzata e si comporta come la **delle proprietà** finestra applicando gli attributi dal <xref:System.ComponentModel> dello spazio dei nomi per la definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che viene visualizzato nei **proprietà** finestra.

- <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione che viene visualizzato in fondo il **proprietà** finestra quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa che viene visualizzata nei **proprietà** finestra e un valore della proprietà non di tipo stringa.

- <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da utilizzare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questi esempi richiedono un progetto libreria di classi con i riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuire l'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida per un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Estendere gli elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
