---
title: Aggiungere la voce di menu di scelta rapida al tipo di elemento di progetto SharePoint personalizzato
titleSuffix: ''
description: Informazioni su come aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato. La voce di menu viene visualizzata quando si fa clic con il pulsante destro del mouse sull'elemento del progetto in Esplora soluzioni.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3e4523d0f992ed72c9af2eb7e542f902578f9338
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215383"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una voce di menu di scelta rapida all'elemento del progetto. La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse sull'elemento del progetto in **Esplora soluzioni**.

 Nei passaggi seguenti si presuppone che sia già stato definito un tipo di elemento di progetto SharePoint personalizzato. Per altre informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Per aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzato

1. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del parametro *ProjectItemTypeDefinition* .

2. Nel gestore eventi per l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oggetto alla <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta o del parametro degli argomenti dell'evento.

3. Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore eventi per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oggetto, eseguire le attività che si desidera eseguire quando un utente sceglie la voce di menu di scelta rapida.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzato. Quando l'utente apre il menu di scelta rapida dall'elemento del progetto in **Esplora soluzioni** e sceglie la voce **di menu scrivi messaggio in finestra di output** , Visual Studio Visualizza un messaggio nella finestra **output** .

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs" id="Snippet4":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb" id="Snippet4":::

 In questo esempio viene utilizzato il servizio di progetto SharePoint per scrivere il messaggio nella finestra di **output** . Per ulteriori informazioni, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un progetto di libreria di classi con riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento di progetto
 Per consentire ad altri sviluppatori di usare l'elemento del progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Per distribuire l'elemento di progetto, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly, il modello e qualsiasi altro file che si vuole distribuire con l'elemento del progetto. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definizione di tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
