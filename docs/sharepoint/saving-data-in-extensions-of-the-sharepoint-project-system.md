---
title: Salvataggio dei dati nelle estensioni del sistema del progetto SharePoint | Microsoft Docs
titleSuffix: ''
description: Informazioni su come salvare i dati di stringa che vengono mantenuti dopo la chiusura di un progetto SharePoint contenente un'estensione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e3c05b9ad570febcfc28fec367a8d180dd2b222
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440649"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Salvare i dati nelle estensioni del sistema di progetto SharePoint
  Quando si estende il sistema del progetto SharePoint, è possibile salvare i dati di stringa che vengono mantenuti dopo la chiusura di un progetto SharePoint. I dati sono in genere associati a un particolare elemento di progetto o al progetto stesso.

 Se sono presenti dati che non devono essere resi persistenti, è possibile aggiungere i dati a qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementi l' <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfaccia. Per altre informazioni, vedere [associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Salvare i dati associati a un elemento del progetto
 Quando si dispone di dati associati a un particolare elemento del progetto SharePoint, ad esempio il valore di una proprietà che si aggiunge a un elemento del progetto, è possibile salvare i dati nel file con *estensione spdata* per l'elemento del progetto. A tale scopo, utilizzare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> oggetto. I dati aggiunti a questa proprietà vengono salvati nell'elemento **ExtensionData** del file con *estensione spdata* per l'elemento del progetto. Per altre informazioni, vedere [elemento ExtensionData](../sharepoint/extensiondata-element.md).

 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà per salvare il valore di una proprietà di stringa definita in un tipo di elemento di progetto SharePoint personalizzato. Per vedere questo esempio nel contesto di un esempio più ampio, vedere [procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Salvare i dati associati a un progetto
 Quando si dispone di dati a livello di progetto, ad esempio il valore di una proprietà aggiunta ai progetti SharePoint, è possibile salvare i dati nel file di progetto (file con estensione *csproj* o *VBPROJ* ) o nel file di opzioni utente del progetto (file con *estensione csproj* o *vbproj. User* ). Il file in cui si sceglie di salvare i dati dipende da come si desidera che vengano utilizzati i dati:

- Se si desidera che i dati siano disponibili per tutti gli sviluppatori che aprono il progetto SharePoint, salvare i dati nel file di progetto. Questo file viene archiviato sempre nei database del controllo del codice sorgente, quindi i dati in questo file sono disponibili per altri sviluppatori che verificano il progetto.

- Se si desidera che i dati siano disponibili solo per lo sviluppatore corrente in cui è aperto il progetto SharePoint in Visual Studio, salvare i dati nel file delle opzioni utente del progetto. Questo file non viene in genere archiviato nei database del controllo del codice sorgente, quindi i dati nel file non sono disponibili ad altri sviluppatori che estraggono il progetto.

### <a name="save-data-to-the-project-file"></a>Salvare i dati nel file di progetto
 Per salvare i dati nel file di progetto, convertire un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> oggetto e quindi usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodo. Nell'esempio di codice riportato di seguito viene illustrato come utilizzare questo metodo per salvare il valore di una proprietà del progetto nel file di progetto. Per vedere questo esempio nel contesto di un esempio più ampio, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Per ulteriori informazioni sulla conversione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> di oggetti in altri tipi nel modello a oggetti di automazione di Visual Studio o nel modello a oggetti di integrazione, vedere eseguire la conversione [tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Salva i dati nel file delle opzioni utente del progetto
 Per salvare i dati nel file di opzioni utente del progetto, usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto. Nell'esempio di codice riportato di seguito viene illustrato come utilizzare questa proprietà per salvare il valore di una proprietà del progetto nel file di opzioni utente del progetto. Per vedere questo esempio nel contesto di un esempio più ampio, vedere [procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Vedere anche
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Conversione tra tipi di sistemi di progetto SharePoint e altri tipi di progetto di Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
