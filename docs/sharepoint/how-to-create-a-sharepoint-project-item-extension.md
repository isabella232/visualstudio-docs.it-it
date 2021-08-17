---
title: "Procedura: Creare un'estensione SharePoint Project elemento | Microsoft Docs"
description: Vedere come creare un'estensione dell'elemento di progetto quando si vuole aggiungere funzionalità a un elemento di progetto SharePoint già installato in Visual Studio.
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
ms.openlocfilehash: 198ae95dabcb65e96a2db6bd60fbfb3667ab2c08
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026980"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Procedura: Creare un'estensione SharePoint elemento di progetto
  Creare un'estensione dell'elemento di progetto quando si vuole aggiungere funzionalità a un SharePoint di progetto già installato in Visual Studio. Per altre informazioni, vedere [Estendere SharePoint di progetto.](../sharepoint/extending-sharepoint-project-items.md)

### <a name="to-create-a-project-item-extension"></a>Per creare un'estensione dell'elemento di progetto

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.

4. Aggiungere gli attributi seguenti alla classe :

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente Visual Studio individuare e caricare <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> l'implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> tipo al costruttore dell'attributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In un'estensione dell'elemento di progetto questo attributo identifica l'elemento di progetto che si vuole estendere. Passare l'ID dell'elemento di progetto al costruttore dell'attributo. Per un elenco degli ID degli elementi di progetto inclusi in Visual Studio, vedere Estendere SharePoint [di progetto.](../sharepoint/extending-sharepoint-project-items.md)

5. Nell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> del metodo usare i membri del *parametro projectItemType* per definire il comportamento dell'estensione. Questo parametro è <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> un oggetto che fornisce l'accesso agli eventi definiti nelle interfacce e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Per accedere a un'istanza specifica del tipo di elemento di progetto che si sta estendendo, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi come <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come creare una semplice estensione per l'elemento di progetto Event Receiver. Ogni volta che l'utente aggiunge un elemento di progetto Ricevitore di eventi a un progetto SharePoint, questa estensione scrive un messaggio nella finestra **Output** e nella **finestra Elenco** errori.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs" id="Snippet1":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb" id="Snippet1":::

 Questo esempio usa il SharePoint servizio di progetto per scrivere il messaggio nella finestra **Output** e nella **finestra Elenco** errori. Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si vuole distribuire con l'estensione. Per altre informazioni, vedere [Deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere SharePoint di progetto](../sharepoint/extending-sharepoint-project-items.md)
- [Procedura dettagliata: Estendere un tipo SharePoint di elemento di progetto](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
