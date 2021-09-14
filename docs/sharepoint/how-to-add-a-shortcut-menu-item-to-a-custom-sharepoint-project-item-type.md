---
title: Aggiungere una voce di menu di scelta rapida al SharePoint tipo di elemento di progetto personalizzato
titleSuffix: ''
description: Informazioni su come aggiungere una voce di menu di scelta rapida a un tipo di elemento SharePoint progetto personalizzato. La voce di menu viene visualizzata quando si fa clic con il pulsante destro del mouse sull'elemento di progetto Esplora soluzioni.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: b966f3a721a9f4330325712c3268f3fe593eb149
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625139"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento SharePoint progetto personalizzato
  Quando si definisce un tipo di SharePoint elemento di progetto personalizzato, è possibile aggiungere una voce di menu di scelta rapida all'elemento di progetto. La voce di menu viene visualizzata quando un utente fa clic con il pulsante destro del mouse sull'elemento di progetto in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stato definito il proprio SharePoint tipo di elemento di progetto. Per altre informazioni, vedere [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Per aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzato

1. Nel metodo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> dell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> l'evento del *parametro projectItemTypeDefinition.*

2. Nel gestore eventi per <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> l'evento aggiungere un nuovo oggetto alla raccolta o del parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> dell'evento.

3. Nel gestore eventi per il nuovo oggetto eseguire le attività da eseguire quando un utente sceglie la <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> voce di menu di scelta <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> rapida.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto personalizzato. Quando l'utente apre il menu di scelta rapida dall'elemento di progetto in **Esplora soluzioni** e sceglie la voce di menu Scrivi messaggio **Finestra di output,** Visual Studio visualizza un messaggio nella finestra **Output.**

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs" id="Snippet4":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb" id="Snippet4":::

 In questo esempio viene SharePoint servizio di progetto per scrivere il messaggio nella **finestra Output.** Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un progetto libreria di classi con riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento di progetto
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [Creare modelli di elemento e modelli di progetto per SharePoint di progetto.](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)

 Per distribuire l'elemento di progetto, creare un pacchetto di estensione (VSIX) per l'assembly, il modello e qualsiasi altro file da distribuire con [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] l'elemento di progetto. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una proprietà a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definizione di tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
