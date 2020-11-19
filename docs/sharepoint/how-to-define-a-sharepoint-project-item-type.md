---
title: 'Procedura: definire un tipo di elemento di progetto SharePoint | Microsoft Docs'
description: Informazioni su come definire un tipo di elemento di progetto quando si desidera creare un elemento di progetto SharePoint personalizzato.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78b10e6878301a878de14306f92f425402e1cc17
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903611"
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Procedura: definire un tipo di elemento di progetto SharePoint
  Definire un tipo di elemento di progetto quando si desidera creare un elemento di progetto SharePoint personalizzato. Per ulteriori informazioni, vedere [definizione di tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md).

### <a name="to-define-a-project-item-type"></a>Per definire un tipo di elemento di progetto

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.

4. Aggiungere gli attributi seguenti alla classe:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo al costruttore dell'attributo.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In una definizione di tipo di elemento di progetto, questo attributo specifica l'identificatore di stringa per il nuovo elemento di progetto. Si consiglia di utilizzare il formato *nome società*. *nome della funzionalità* che consente di verificare che tutti gli elementi del progetto abbiano un nome univoco.

    - <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Questo attributo specifica l'icona da visualizzare per questo elemento del progetto in **Esplora soluzioni**. Questo attributo è facoltativo. Se non lo si applica alla classe, Visual Studio Visualizza un'icona predefinita per l'elemento del progetto. Se si imposta questo attributo, passare il nome completo di un'icona o di una bitmap incorporata nell'assembly.

5. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo usare i membri del parametro *ProjectItemTypeDefinition* per definire il comportamento del tipo di elemento del progetto. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> oggetto che fornisce l'accesso agli eventi definiti nelle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> interfacce e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> . Per accedere a un'istanza specifica del tipo di elemento del progetto, gestire <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventi quali <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized> .

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come definire un tipo di elemento di progetto semplice. Questo tipo di elemento di progetto scrive un messaggio nella finestra di **output** e **Elenco errori** finestra quando un utente aggiunge un elemento di progetto di questo tipo a un progetto.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]

 In questo esempio viene utilizzato il servizio di progetto SharePoint per scrivere il messaggio nella finestra di **output** e **Elenco errori** finestra. Per ulteriori informazioni, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento di progetto
 Per consentire ad altri sviluppatori di usare l'elemento del progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [creare modelli di elementi e modelli di progetto per gli elementi del progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Per distribuire l'elemento di progetto, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly, il modello e qualsiasi altro file che si vuole distribuire con l'elemento del progetto. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Definire i tipi di elementi di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Creare modelli di elementi e modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Procedura dettagliata: creare un elemento di progetto azione personalizzata con un modello di elemento, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Procedura dettagliata: creare un elemento di progetto colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Procedura: aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Procedura: aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
