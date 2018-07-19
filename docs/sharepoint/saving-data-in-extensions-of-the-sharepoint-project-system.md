---
title: Salvataggio dei dati nelle estensioni del sistema del progetto SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 74228b5259b733c91397eb1b40a2485daea8b79e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118976"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Salvare i dati nelle estensioni del sistema del progetto SharePoint
  Quando si estende il sistema di progetto SharePoint, è possibile salvare i dati di stringa che persiste dopo la chiusura di un progetto SharePoint. I dati sono in genere associato a un elemento di progetto specifico o con il progetto stesso.  
  
 Se sono presenti dati che non sono necessario rendere persistenti, è possibile aggiungere i dati in qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa il <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaccia. Per altre informazioni, vedere [estensioni degli strumenti di associazione dati personalizzati con SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="save-data-that-is-associated-with-a-project-item"></a>Salvare i dati associati a un elemento del progetto
 Quando sono presenti dati che sono associati a un particolare elemento di progetto SharePoint, ad esempio il valore di una proprietà che aggiunta a un elemento del progetto, è possibile salvare i dati per il *spdata* file per l'elemento del progetto. A questo scopo, usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto. I dati aggiunti a questa proprietà viene salvati nel **ExtensionData** elemento il *spdata* file per l'elemento del progetto. Per altre informazioni, vedere [elemento ExtensionData](../sharepoint/extensiondata-element.md).  
  
 Esempio di codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per salvare il valore di una proprietà stringa che viene definito in un tipo di elemento di progetto SharePoint personalizzato. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="save-data-that-is-associated-with-a-project"></a>Salvare i dati associati a un progetto
 Quando si dispone di dati a livello di progetto, ad esempio il valore di una proprietà che aggiunta ai progetti SharePoint, è possibile salvare i dati del file di progetto (il *file con estensione csproj* file o *vbproj* file) o l'opzione di progetto utente file (il *. csproj* file o *. vbproj* file). Il file in che si sceglie di salvare i dati dipende dal modo in cui i dati da utilizzare:  
  
-   Se si desidera che i dati siano disponibili per tutti gli sviluppatori che aprono il progetto di SharePoint, è possibile salvare i dati del file di progetto. Questo file viene sempre archiviato nel database di controllo di origine, in modo che i dati in questo file sono disponibili per gli sviluppatori che estraggono il progetto.  
  
-   Se si desidera che i dati siano disponibili solo per lo sviluppatore corrente che ha il progetto SharePoint aperto in Visual Studio, è possibile salvare i dati del file di progetto utente opzione. Questo file non è in genere archiviato nel database di controllo di origine, in modo che i dati in questo file non sono disponibili per gli sviluppatori che estraggono il progetto.  
  
### <a name="save-data-to-the-project-file"></a>Salvare i dati del file di progetto
 Per salvare i dati del file di progetto, convertire un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> dell'oggetto a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> dell'oggetto e quindi usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> (metodo). Esempio di codice seguente viene illustrato come utilizzare questo metodo per salvare il valore di una proprietà di progetto per il file di progetto. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Per altre informazioni sulla conversione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> degli oggetti in altri tipi nel modello oggetto di automazione di Visual Studio o nel modello oggetto di integrazione, vedere [eseguire la conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="save-data-to-the-project-user-option-file"></a>Salvare i dati del file di progetto utente opzione
 Per salvare i dati del file di progetto utente opzione, usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto. Esempio di codice seguente viene illustrato come utilizzare questa proprietà per salvare il valore di una proprietà del progetto al file delle opzioni utente del progetto. Per questo esempio nel contesto di un esempio più esaustivo, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Vedere anche
 [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Eseguire la conversione tra tipi di sistema di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
