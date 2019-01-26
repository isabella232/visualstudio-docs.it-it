---
title: "Procedura: Aggiungere una voce di Menu di scelta rapida per un'estensione di elemento di progetto SharePoint | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4502d938b9f268c389e224fe9040a99d24516d77
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869329"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Procedura: Aggiungere una voce di menu di scelta rapida per un'estensione di elemento di progetto SharePoint
  È possibile aggiungere una voce di menu di scelta rapida a un elemento di progetto SharePoint esistente usando un'estensione di elemento di progetto. La voce di menu viene visualizzato quando l'utente fa clic l'elemento del progetto in **Esplora soluzioni**.  
  
 I passaggi seguenti presuppongono che un'estensione di elemento di progetto è già stato creato. Per altre informazioni, vedere [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Per aggiungere una voce di menu di scelta rapida in un'estensione di elemento di progetto  
  
1.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo delle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del *projectItemType* parametro.  
  
2.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta del parametro di argomenti dell'evento.  
  
3.  Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore dell'evento per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto, eseguire le attività da eseguire quando un utente sceglie la voce di menu di scelta rapida.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida per l'elemento di progetto del ricevitore di eventi. Quando l'utente fa clic l'elemento del progetto in **Esplora soluzioni** e fa clic il **scrivere messaggi finestra di Output** voce di menu, Visual Studio visualizza un messaggio nel **Output**finestra.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 Questo esempio Usa il servizio di progetto SharePoint in cui per scrivere il messaggio il **Output** finestra. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio richiede un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Distribuire l'estensione  
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Procedura: Aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Estendere gli elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procedura dettagliata: Estendere un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
