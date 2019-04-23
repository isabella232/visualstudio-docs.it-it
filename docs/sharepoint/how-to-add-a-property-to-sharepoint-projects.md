---
title: 'Procedura: Aggiungere una proprietà ai progetti SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a6f1ecd427b1c715649bc2118be5ab384a74c585
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084312"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Procedura: Aggiungere una proprietà ai progetti SharePoint
  È possibile utilizzare un'estensione di progetto per aggiungere una proprietà a qualsiasi progetto SharePoint. La proprietà viene visualizzata nel **delle proprietà** finestra quando il progetto sia selezionato **Esplora soluzioni**.

 I passaggi seguenti presuppongono che un'estensione di progetto è già stato creato. Per altre informazioni, vedere [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Per aggiungere una proprietà a un progetto SharePoint

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere ai progetti SharePoint. Se si desidera aggiungere più proprietà, è possibile definire tutte le proprietà della stessa classe o in diverse classi.

2. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo delle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento del *projectService* parametro.

3. Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento, aggiungere un'istanza della classe di proprietà per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro di argomenti dell'evento.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come aggiungere due proprietà ai progetti SharePoint. Una proprietà mantiene i relativi dati nel file delle opzioni utente del progetto (il *. csproj* file o *. vbproj* file). L'altra proprietà mantiene i relativi dati nel file di progetto (*file con estensione csproj* file o *vbproj* file).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Informazioni sul codice
 Per garantire che la stessa istanza del `CustomProjectProperties` classe viene utilizzata ogni volta che il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento si verifica, l'esempio di codice aggiunge l'oggetto delle proprietà per il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà di progetto la prima volta che questo evento viene generato. Il codice recupera l'oggetto ogni volta che questo evento viene generato nuovamente. Per altre informazioni sull'uso di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per associare i dati con i progetti, vedere [estensioni degli strumenti di associazione dati personalizzati con SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Per rendere persistenti le modifiche ai valori della proprietà, il **impostare** funzioni di accesso per le proprietà utilizzare le API seguenti:

- `CustomUserFileProperty` Usa il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà per salvare il relativo valore per il file delle opzioni progetto utente.

- `CustomProjectFileProperty` Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodo per salvare il relativo valore nel file di progetto.

  Per altre informazioni sulla persistenza dei dati in questi file, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire come una proprietà personalizzata viene visualizzata e si comporta come la **delle proprietà** finestra applicando gli attributi dal <xref:System.ComponentModel> dello spazio dei nomi per la definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che viene visualizzato nei **proprietà** finestra.

- <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione che viene visualizzato in fondo il **proprietà** finestra quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa che viene visualizzata nei **proprietà** finestra e un valore della proprietà non di tipo stringa.

- <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da utilizzare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.Shell

- Microsoft.VisualStudio.Shell.Interop

- Microsoft.VisualStudio.Shell.Interop.8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuire l'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Estendere i progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: Creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
