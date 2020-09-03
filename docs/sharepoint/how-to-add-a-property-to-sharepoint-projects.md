---
title: 'Procedura: aggiungere una proprietà ai progetti SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: eb72b0546b504e2df1a7e93ea9d4def350143d1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015925"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Procedura: aggiungere una proprietà ai progetti SharePoint
  È possibile utilizzare un'estensione di progetto per aggiungere una proprietà a qualsiasi progetto SharePoint. La proprietà viene visualizzata nella finestra **Proprietà** quando il progetto è selezionato in **Esplora soluzioni**.

 Nei passaggi seguenti si presuppone che sia già stata creata un'estensione di progetto. Per altre informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Per aggiungere una proprietà a un progetto SharePoint

1. Definire una classe con una proprietà pubblica che rappresenti la proprietà che si sta aggiungendo ai progetti SharePoint. Se si desidera aggiungere più proprietà, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.

2. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento del parametro *ProjectService* .

3. Nel gestore eventi per l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> evento, aggiungere un'istanza della classe Properties alla <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> raccolta del parametro degli argomenti dell'evento.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere due proprietà ai progetti SharePoint. Una proprietà rende permanente i dati nel file di opzioni utente del progetto (file con *estensione csproj. User* o *vbproj. User* ). L'altra proprietà rende permanente i dati nel file di progetto (file con estensione*csproj* o *VBPROJ* ).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Informazioni sul codice
 Per assicurarsi che venga utilizzata la stessa istanza della `CustomProjectProperties` classe ogni volta che <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> si verifica l'evento, l'esempio di codice aggiunge l'oggetto Properties alla <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà del progetto la prima volta che si verifica questo evento. Il codice recupera questo oggetto ogni volta che l'evento si verifica di nuovo. Per ulteriori informazioni sull'utilizzo della <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà per associare i dati ai progetti, vedere [associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Per salvare in modo permanente le modifiche apportate ai valori delle proprietà, le funzioni di accesso **set** per le proprietà utilizzano le API seguenti:

- `CustomUserFileProperty` Usa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà per salvare il valore nel file di opzioni utente del progetto.

- `CustomProjectFileProperty` Usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodo per salvare il valore nel file di progetto.

  Per ulteriori informazioni sulla conservazione dei dati in questi file, vedere [salvare i dati nelle estensioni del sistema del progetto SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire il modo in cui una proprietà personalizzata viene visualizzata e si comporta nella finestra **Proprietà** applicando gli attributi dello <xref:System.ComponentModel> spazio dei nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: Specifica il nome della proprietà che viene visualizzata nella finestra **Proprietà** .

- <xref:System.ComponentModel.DescriptionAttribute>: Specifica la stringa di descrizione visualizzata nella parte inferiore della finestra **Proprietà** quando la proprietà è selezionata.

- <xref:System.ComponentModel.DefaultValueAttribute>: Specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: Specifica una conversione personalizzata tra la stringa visualizzata nella finestra **Proprietà** e un valore di proprietà non stringa.

- <xref:System.ComponentModel.EditorAttribute>: Specifica un editor personalizzato da usare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Estensione di progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
