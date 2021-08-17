---
title: 'Procedura: Aggiungere una voce di menu di scelta rapida SharePoint progetti | Microsoft Docs'
titleSuffix: ''
description: Aggiungere una voce di menu di scelta rapida a SharePoint progetto in Visual Studio. La voce di menu viene visualizzata quando si fa clic con il pulsante destro del mouse su un nodo di progetto Esplora soluzioni.
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
ms.openlocfilehash: df2baff33b1eaa56a8d595fb95a6f46cf7d811a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027032"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Procedura: Aggiungere una voce di menu di scelta rapida SharePoint progetti
  È possibile aggiungere una voce di menu di scelta rapida a qualsiasi SharePoint progetto. La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse su un nodo di progetto in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stata creata un'estensione di progetto. Per altre informazioni, vedere [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Per aggiungere una voce di menu di scelta rapida SharePoint progetti

1. Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> dell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> l'evento del *parametro projectService.*

2. Nel gestore eventi per <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> l'evento aggiungere un nuovo oggetto alla raccolta o del parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> dell'evento.

3. Nel gestore eventi per il nuovo oggetto eseguire le attività che si desidera eseguire quando un utente fa clic sulla <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> voce di menu di scelta <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> rapida.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida SharePoint nodi del progetto in **Esplora soluzioni**. Quando l'utente fa clic con il pulsante destro del mouse su un nodo di progetto e fa clic sulla voce di **menu** Finestra di output, Visual Studio visualizza un messaggio nella **finestra Output.** In questo esempio viene utilizzata SharePoint servizio di progetto per visualizzare il messaggio. Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un progetto libreria di classi con riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si vuole distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint progetti](../sharepoint/extending-sharepoint-projects.md)
- [Procedura: Creare un'estensione SharePoint progetto](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Procedura: Aggiungere una proprietà a SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
