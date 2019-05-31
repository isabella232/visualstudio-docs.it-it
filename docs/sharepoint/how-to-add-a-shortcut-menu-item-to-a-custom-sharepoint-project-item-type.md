---
title: Aggiungi voce di menu di scelta rapida per tipo di elemento di progetto SharePoint personalizzato
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 95c47cdc00fc9035870aed4ac2e0bee4d3c1c5af
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401627"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Procedura: Aggiungere una voce di menu di scelta rapida a un tipo di elemento di progetto SharePoint personalizzato
  Quando si definisce un tipo di elemento di progetto SharePoint personalizzato, è possibile aggiungere una voce di menu di scelta rapida per l'elemento del progetto. La voce di menu viene visualizzato quando l'utente fa clic l'elemento del progetto in **Esplora soluzioni**.

 I passaggi seguenti presuppongono che sia già stata definita il proprio tipo di elemento di progetto SharePoint. Per altre informazioni, vedere [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Per aggiungere una voce di menu di scelta rapida per un tipo di elemento di progetto personalizzati

1. Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo delle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del *projectItemTypeDefinition* parametro.

2. Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta del parametro di argomenti dell'evento.

3. Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore dell'evento per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto, eseguire le attività da eseguire quando un utente sceglie la voce di menu di scelta rapida.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come aggiungere un menu di scelta rapida a un tipo di elemento di progetto personalizzato. Quando l'utente apre il menu di scelta rapida dall'elemento del progetto in **Esplora soluzioni** e sceglie il **scrittura di messaggi alla finestra di Output** voce di menu, Visual Studio visualizza un messaggio nel **Output**  finestra.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 Questo esempio Usa il servizio di progetto SharePoint in cui per scrivere il messaggio il **Output** finestra. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio richiede un progetto libreria di classi con i riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Distribuire l'elemento del progetto
 Per consentire ad altri sviluppatori di usare l'elemento di progetto, creare un modello di progetto o un modello di elemento di progetto. Per altre informazioni, vedere [creare elementi di modelli e i modelli di progetto per gli elementi di progetto SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Per distribuire l'elemento del progetto, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly, il modello e qualsiasi altro file che si desidera distribuire con l'elemento del progetto. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Procedura: Aggiungere una proprietà a un tipo di elemento di progetto SharePoint personalizzato](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definizione di tipi di elemento di progetto SharePoint personalizzati](../sharepoint/defining-custom-sharepoint-project-item-types.md)
