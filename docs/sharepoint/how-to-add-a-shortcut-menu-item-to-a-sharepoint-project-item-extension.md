---
title: Aggiungere la voce di menu di scelta rapida all'estensione dell'elemento di progetto SharePoint
titleSuffix: ''
description: Aggiungere una voce di menu di scelta rapida a un elemento del progetto SharePoint esistente usando un'estensione di elemento del progetto in Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bac5ff10ea59ba422a9dc33855919eb999a996ee
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215396"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Procedura: aggiungere una voce di menu di scelta rapida a un'estensione di elemento di progetto SharePoint
  È possibile aggiungere una voce di menu di scelta rapida a un elemento del progetto SharePoint esistente utilizzando un'estensione di elemento del progetto. La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse sull'elemento del progetto in **Esplora soluzioni**.

 Nei passaggi seguenti si presuppone che sia già stata creata un'estensione di elemento di progetto. Per altre informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Per aggiungere una voce di menu di scelta rapida in un'estensione di elemento del progetto

1. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione, gestire l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del parametro *projectItemType* .

2. Nel gestore eventi per l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oggetto alla <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta o del parametro degli argomenti dell'evento.

3. Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore eventi per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> oggetto, eseguire le attività che si desidera eseguire quando un utente fa clic sulla voce di menu di scelta rapida.

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere una voce di menu di scelta rapida all'elemento del progetto ricevitore di eventi. Quando l'utente fa clic con il pulsante destro del mouse sull'elemento del progetto in **Esplora soluzioni** e fa clic sulla voce **di menu Scrivi messaggio finestra di output** , Visual Studio Visualizza un messaggio nella finestra **output** .

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs" id="Snippet1":::

 In questo esempio viene utilizzato il servizio di progetto SharePoint per scrivere il messaggio nella finestra di **output** . Per ulteriori informazioni, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un progetto di libreria di classi con riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si vuole distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Estendi elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
