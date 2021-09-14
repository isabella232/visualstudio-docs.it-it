---
title: Aggiungere una voce di menu di scelta rapida SharePoint'estensione dell'elemento di progetto
titleSuffix: ''
description: Aggiungere una voce di menu di scelta rapida a un elemento SharePoint progetto esistente usando un'estensione dell'elemento di progetto in Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c50f6b763aa8a56aa1049c1d0394f9878a39fe83
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625140"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Procedura: Aggiungere una voce di menu di scelta rapida a un'SharePoint dell'elemento di progetto
  È possibile aggiungere una voce di menu di scelta rapida a un SharePoint progetto esistente usando un'estensione dell'elemento di progetto. La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse sull'elemento di progetto in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stata creata un'estensione dell'elemento di progetto. Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Per aggiungere una voce di menu di scelta rapida in un'estensione di elemento di progetto

1. Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> dell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> l'evento del *parametro projectItemType.*

2. Nel gestore eventi per <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> l'evento aggiungere un nuovo oggetto alla raccolta o del parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> dell'evento.

3. Nel gestore eventi per il nuovo oggetto eseguire le attività che si desidera eseguire quando un utente fa clic sulla <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> voce di menu di scelta <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> rapida.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida alla voce di progetto Ricevitore di eventi. Quando l'utente fa clic con il pulsante destro del mouse sull'elemento di progetto in **Esplora soluzioni** e fa clic sulla voce di menu Write **Message to Finestra di output** (Scrivi messaggio Finestra di output), Visual Studio visualizza un messaggio nella finestra **Output.**

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb" id="Snippet1":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs" id="Snippet1":::

 In questo esempio viene SharePoint servizio di progetto per scrivere il messaggio nella **finestra Output.** Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un progetto libreria di classi con riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si vuole distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un'estensione SharePoint elemento di progetto](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Procedura: Aggiungere una proprietà a un'estensione SharePoint elemento di progetto](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
