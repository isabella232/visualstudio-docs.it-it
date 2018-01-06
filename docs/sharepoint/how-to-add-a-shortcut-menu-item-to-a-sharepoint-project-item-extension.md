---
title: 'Procedura: aggiungere una voce di Menu di scelta rapida per un''estensione di elemento di progetto SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 63c19f3335b95cfe26d87f2fbf210e4033606538
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Procedura: aggiungere una voce di menu di scelta rapida a un'estensione di elemento di progetto SharePoint
  È possibile aggiungere una voce di menu di scelta rapida a un elemento di progetto SharePoint esistente utilizzando un'estensione di elemento di progetto. La voce di menu viene visualizzata quando l'utente fa clic l'elemento del progetto in **Esplora**.  
  
 I passaggi seguenti presuppongono che un'estensione di elemento di progetto è già stato creato. Per ulteriori informazioni, vedere [procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Per aggiungere una voce di menu di scelta rapida in un'estensione di elemento di progetto  
  
1.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodo i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del *projectItemType* parametro.  
  
2.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta del parametro di argomenti dell'evento.  
  
3.  Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore eventi per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto, eseguire le attività da eseguire quando un utente fa clic sulla voce di menu di scelta rapida.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida per l'elemento del progetto ricevitore di eventi. Quando l'utente fa l'elemento del progetto in **Esplora** e fa clic su di **scrivere messaggi nella finestra di Output** voce di menu, Visual Studio viene visualizzato un messaggio nel **Output**finestra.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]  
  
 In questo esempio viene utilizzato il servizio di progetto SharePoint in cui per scrivere il messaggio di **Output** finestra. Per ulteriori informazioni, vedere [utilizza il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire l'estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Procedura: aggiungere una proprietà a un'estensione di elemento di progetto SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Estensione di elementi di progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Procedura dettagliata: estensione di un tipo di elemento di progetto SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  