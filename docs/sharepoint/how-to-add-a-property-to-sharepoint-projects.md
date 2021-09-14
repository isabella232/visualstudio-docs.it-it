---
title: 'Procedura: Aggiungere una proprietà per SharePoint progetti | Microsoft Docs'
description: Usare un'estensione di progetto per aggiungere una proprietà a un SharePoint progetto. Quando si seleziona il progetto in Esplora soluzioni, viene visualizzata una proprietà Finestra Proprietà.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9daebc52f63acdf6e165ea162c90189fab534193
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625146"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Procedura: Aggiungere una proprietà ai SharePoint progetto
  È possibile usare un'estensione di progetto per aggiungere una proprietà a qualsiasi SharePoint progetto. La proprietà viene visualizzata nella **finestra Proprietà** quando il progetto viene selezionato in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stata creata un'estensione di progetto. Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint progetto .](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Per aggiungere una proprietà a un SharePoint progetto

1. Definire una classe con una proprietà pubblica che rappresenta la proprietà da aggiungere SharePoint progetti. Se si desidera aggiungere più proprietà, è possibile definire tutte le proprietà nella stessa classe o in classi diverse.

2. Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> dell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> l'evento del *parametro projectService.*

3. Nel gestore eventi per <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> l'evento aggiungere un'istanza della classe properties alla raccolta del parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> dell'evento.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come aggiungere due proprietà SharePoint progetti. Una proprietà rende persistenti i dati nel file delle opzioni utente del progetto (file *con estensione csproj.user* o *vbproj.user).* L'altra proprietà rende persistenti i dati nel file di progetto (file *con estensione csproj* o *vbproj).*

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet1":::

### <a name="understand-the-code"></a>Informazioni sul codice
 Per assicurarsi che la stessa istanza della classe sia utilizzata ogni volta che si verifica l'evento , l'esempio di codice aggiunge l'oggetto proprietà alla proprietà del progetto la prima volta che si `CustomProjectProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> verifica questo <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> evento. Il codice recupera questo oggetto ogni volta che si verifica di nuovo questo evento. Per altre informazioni sull'uso della proprietà per associare i dati ai progetti, vedere Associare dati personalizzati <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [SharePoint estensioni degli strumenti.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

 Per rendere persistenti le modifiche ai valori delle proprietà, le funzioni di accesso **set** per le proprietà usano le API seguenti:

- `CustomUserFileProperty` usa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà per salvare il valore nel file di opzioni utente del progetto.

- `CustomProjectFileProperty` usa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodo per salvare il relativo valore nel file di progetto.

  Per altre informazioni sulla persistenza dei dati in questi file, vedere Salvare i dati nelle estensioni del [sistema SharePoint progetto](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Specificare il comportamento delle proprietà personalizzate
 È possibile definire l'aspetto e il  comportamento di una proprietà personalizzata nella finestra Proprietà applicando gli attributi dello spazio dei <xref:System.ComponentModel> nomi alla definizione della proprietà. Gli attributi seguenti sono utili in molti scenari:

- <xref:System.ComponentModel.DisplayNameAttribute>: specifica il nome della proprietà visualizzata nella **finestra** Proprietà.

- <xref:System.ComponentModel.DescriptionAttribute>: specifica la stringa di descrizione visualizzata nella parte inferiore **della** finestra Proprietà quando viene selezionata la proprietà .

- <xref:System.ComponentModel.DefaultValueAttribute>: specifica il valore predefinito della proprietà.

- <xref:System.ComponentModel.TypeConverterAttribute>: specifica una conversione personalizzata tra la  stringa visualizzata nella finestra Proprietà e un valore di proprietà non stringa.

- <xref:System.ComponentModel.EditorAttribute>: specifica un editor personalizzato da utilizzare per modificare la proprietà.

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- Microsoft.visualstudio.shell

- Microsoft.VisualStudio.Shell.Interop

- Microsoft.VisualStudio.Shell.Interop.8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint progetti](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida SharePoint progetti](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Estendere il SharePoint di progetto](../sharepoint/extending-the-sharepoint-project-system.md)
