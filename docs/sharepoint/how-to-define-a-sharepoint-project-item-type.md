---
title: 'Procedura: Definire un tipo SharePoint Project elemento | Microsoft Docs'
description: Informazioni su come definire un tipo di elemento di progetto quando si vuole creare un elemento SharePoint progetto.
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
ms.openlocfilehash: 8d990658c669cd1e22927bc4ae95382def29defa
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636876"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Procedura: Definire un tipo di SharePoint di progetto
  Definire un tipo di elemento di progetto quando si vuole creare un elemento SharePoint progetto. Per altre informazioni, vedere [Definizione di tipi di elemento SharePoint progetto](../sharepoint/defining-custom-sharepoint-project-item-types.md)personalizzati .

### <a name="to-define-a-project-item-type"></a>Per definire un tipo di elemento di progetto

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.

4. Aggiungere gli attributi seguenti alla classe :

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente Visual Studio individuare e caricare <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> l'implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo al costruttore dell'attributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In una definizione del tipo di elemento di progetto questo attributo specifica l'identificatore di stringa per il nuovo elemento di progetto. È consigliabile usare il formato nome *società*. *nome della funzionalità* per assicurarsi che tutti gli elementi di progetto hanno un nome univoco.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Questo attributo specifica l'icona da visualizzare per questo elemento di progetto in **Esplora soluzioni**. Questo attributo è facoltativo. se non si applica alla classe, Visual Studio un'icona predefinita per l'elemento di progetto. Se si imposta questo attributo, passare il nome completo di un'icona o di una bitmap incorporata nell'assembly.

5. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo usare i membri del parametro *projectItemTypeDefinition* per definire il comportamento del tipo di elemento di progetto. Questo parametro è <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> un oggetto che fornisce l'accesso agli eventi definiti nelle interfacce e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Per accedere a un'istanza specifica del tipo di elemento di progetto, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi come <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come definire un tipo di elemento di progetto semplice. Questo tipo di elemento di progetto scrive un messaggio nella finestra **Output** e nella finestra **Elenco** errori quando un utente aggiunge un elemento di progetto di questo tipo a un progetto.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb" id="Snippet2":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs" id="Snippet2":::

 In questo esempio viene SharePoint servizio di progetto per scrivere il messaggio nella finestra **Output** e **nella finestra Elenco** errori. Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento di progetto
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Per distribuire l'elemento di progetto, creare un pacchetto di estensione (VSIX) per l'assembly, il modello e qualsiasi altro file che si [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] vuole distribuire con l'elemento di progetto. Per altre informazioni, vedere [Deploy Extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Definire tipi di SharePoint di progetto personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elemento e modelli di progetto per SharePoint di progetto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procedura dettagliata: Creare un elemento di progetto di azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: Creare un elemento di progetto di colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura: Aggiungere una proprietà a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento SharePoint progetto personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
