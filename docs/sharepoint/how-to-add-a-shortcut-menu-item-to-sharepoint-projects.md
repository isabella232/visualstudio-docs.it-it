---
title: 'Procedura: aggiungere una voce di Menu di scelta rapida ai progetti SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a2fbc9d71684bc44e01a1d53f5d53f35c8d7311
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757572"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Procedura: aggiungere una voce di menu di scelta rapida ai progetti SharePoint
  È possibile aggiungere una voce di menu di scelta rapida per qualsiasi progetto SharePoint. La voce di menu viene visualizzato quando l'utente fa clic in un nodo del progetto **Esplora soluzioni**.  
  
 I passaggi seguenti presuppongono che un'estensione di progetto è già stato creato. Per altre informazioni, vedere [procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Per aggiungere una voce di menu di scelta rapida ai progetti SharePoint  
  
1.  Nel <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo delle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementazione, handle il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento del *projectService* parametro.  
  
2.  Nel gestore eventi per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, aggiungere un nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto per il <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> raccolta del parametro di argomenti dell'evento.  
  
3.  Nel <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> gestore dell'evento per il nuovo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> dell'oggetto, eseguire le attività da eseguire quando un utente sceglie la voce di menu di scelta rapida.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente viene illustrato come aggiungere una voce di menu di scelta rapida per i nodi di progetto SharePoint in **Esplora soluzioni**. Quando l'utente fa clic di un nodo del progetto e fa clic il **scrivere messaggi finestra di Output** voce di menu, Visual Studio visualizza un messaggio nel **Output** finestra. Questo esempio Usa il servizio di progetto SharePoint per visualizzare il messaggio. Per altre informazioni, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 In questo esempio richiede un progetto libreria di classi con i riferimenti agli assembly seguenti:  
  
-   Microsoft.VisualStudio.SharePoint
-     
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Distribuire l'estensione  
 Per distribuire l'estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Estendere i progetti SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Procedura: creare un'estensione di progetto SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Procedura: aggiungere una proprietà ai progetti SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
