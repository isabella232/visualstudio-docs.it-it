---
title: 'Procedura: recuperare dati per un nodo SharePoint incorporato in Esplora Server | Documenti Microsoft'
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa518bf566671dda2b54489fa37460840365bc70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Procedura: ottenere dati per un nodo SharePoint incorporato in Esplora server
  Per ogni nodo SharePoint incorporato in **Esplora Server**, è possibile ottenere dati per il componente SharePoint sottostante che rappresenta il nodo. Per ulteriori informazioni, vedere [estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Esempio  
 Esempio di codice riportato di seguito viene illustrato come ottenere i dati per l'elenco SharePoint sottostante che rappresenta un nodo di elenco in **Esplora Server**. Per impostazione predefinita, i nodi di elenco presentano un **Visualizza nel Browser** voce di menu di contesto che è possibile fare clic per aprire gli elenchi in un Web browser. In questo esempio estende nodi elenco aggiungendo un **visualizzazione in Visual Studio** voce di menu di contesto che consente di aprire gli elenchi direttamente in Visual Studio. Il codice accede a dati di elenco per il nodo ottenere l'URL dell'elenco per aprire in Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 In questo esempio viene utilizzato il servizio di progetto SharePoint per ottenere il <xref:EnvDTE.DTE> Elenca oggetto utilizzato per aprire in Visual Studio. Per ulteriori informazioni sul servizio di progetto SharePoint, vedere [utilizza il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Per ulteriori informazioni sulle attività di base per creare un'estensione per un nodo SharePoint, vedere [procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 Questo esempio richiede riferimenti agli assembly seguenti:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Distribuzione dell'estensione  
 Per distribuire il **Esplora Server** estensione, creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) per l'assembly e altri file che si desiderano distribuire con l'estensione del pacchetto. Per ulteriori informazioni, vedere [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Procedura: estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Utilizzo del servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  