---
title: Salvataggio dei dati nelle estensioni del SharePoint Project di | Microsoft Docs
titleSuffix: ''
description: Informazioni su come salvare i dati stringa che vengono mantenuti dopo la chiusura di un progetto SharePoint che contiene un'estensione.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 671571551483c4eff71c1324e1c53c7cbb43ff9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084051"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Salvare i dati nelle estensioni del sistema SharePoint progetto
  Quando si estende il SharePoint di progetto, è possibile salvare i dati stringa che vengono mantenuti dopo la chiusura SharePoint progetto. I dati sono in genere associati a un particolare elemento di progetto o al progetto stesso.

 Se si dispone di dati che non devono essere mantenuti, è possibile aggiungere i dati a qualsiasi oggetto nel modello a oggetti degli strumenti di SharePoint che implementa <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> l'interfaccia . Per altre informazioni, vedere [Associare dati personalizzati alle estensioni SharePoint tools.](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)

## <a name="save-data-that-is-associated-with-a-project-item"></a>Salvare i dati associati a un elemento di progetto
 Quando si dispone di dati associati a un particolare elemento di progetto SharePoint, ad esempio il valore di una proprietà aggiunta a un elemento di progetto, è possibile salvare i dati nel file con estensione *spdata* per l'elemento di progetto. A tale scopo, usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> proprietà di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> . I dati aggiunti a questa proprietà vengono salvati **nell'elemento ExtensionData** nel file *con estensione spdata* per l'elemento di progetto. Per altre informazioni, vedere [Elemento ExtensionData.](../sharepoint/extensiondata-element.md)

 Nell'esempio di codice seguente viene illustrato come utilizzare la proprietà per salvare il valore di una proprietà stringa definita in un tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> di elemento SharePoint progetto personalizzato. Per visualizzare questo esempio nel contesto di un esempio più ampio, vedere Procedura: Aggiungere una proprietà a un tipo di [elemento SharePoint progetto personalizzato.](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb" id="Snippet14":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs" id="Snippet14":::

## <a name="save-data-that-is-associated-with-a-project"></a>Salvare i dati associati a un progetto
 Quando si dispone di dati a livello di progetto, ad esempio il valore di una proprietà aggiunta ai progetti SharePoint, è possibile salvare i dati nel file di progetto (file con estensione *csproj* o *vbproj)* o nel file delle opzioni utente del progetto (file con estensione *csproj.user* o *vbproj.user).* Il file in cui si sceglie di salvare i dati dipende dalla modalità di utilizzo dei dati:

- Se si vuole che i dati siano disponibili per tutti gli sviluppatori che aprono il SharePoint, salvare i dati nel file di progetto. Questo file viene sempre archiviato nei database del controllo del codice sorgente, quindi i dati in questo file sono disponibili per altri sviluppatori che estraeno il progetto.

- Se si vuole che i dati siano disponibili solo per lo sviluppatore corrente con il progetto SharePoint aperto in Visual Studio, salvare i dati nel file di opzioni utente del progetto. Questo file in genere non viene archiviato nei database del controllo del codice sorgente, quindi i dati in questo file non sono disponibili per altri sviluppatori che estraeno il progetto.

### <a name="save-data-to-the-project-file"></a>Salvare i dati nel file di progetto
 Per salvare i dati nel file di progetto, convertire un oggetto in un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> oggetto e quindi usare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> . Nell'esempio di codice seguente viene illustrato come utilizzare questo metodo per salvare il valore di una proprietà del progetto nel file di progetto. Per visualizzare questo esempio nel contesto di un esempio più ampio, vedere [Procedura: Aggiungere una proprietà a SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet3":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet3":::

 Per altre informazioni sulla conversione di oggetti in altri tipi nel modello a oggetti di automazione di Visual Studio o nel modello a oggetti di integrazione, vedere Eseguire la conversione tra tipi di sistema del progetto SharePoint e altri tipi di progetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> [Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Salvare i dati nel file di opzioni utente del progetto
 Per salvare i dati nel file di opzioni utente del progetto, usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> proprietà di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> . Nell'esempio di codice seguente viene illustrato come utilizzare questa proprietà per salvare il valore di una proprietà del progetto nel file di opzioni utente del progetto. Per visualizzare questo esempio nel contesto di un esempio più ampio, vedere [Procedura: Aggiungere una proprietà a SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs" id="Snippet2":::

## <a name="see-also"></a>Vedi anche
- [Estendere il SharePoint del progetto](../sharepoint/extending-the-sharepoint-project-system.md)
- [Associare dati personalizzati alle estensioni SharePoint tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Eseguire la conversione SharePoint tipi di sistema del progetto e altri Visual Studio tipi di progetto](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
