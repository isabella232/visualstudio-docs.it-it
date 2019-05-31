---
title: Ottenere i dati per nodo SharePoint incorporato in Esplora Server
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b90582c9b8d352f95d3d5abb3bbb7fb69283b06b
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401415"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Procedura: Ottenere i dati per un nodo SharePoint incorporato in Esplora Server
  Per ogni nodo SharePoint incorporato in **Esplora Server**, è possibile ottenere dati per il componente di SharePoint sottostante rappresentata dal nodo. Per altre informazioni, vedere [estendere del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come ottenere dati per l'elenco di SharePoint sottostante che rappresenta un nodo di elenco nel **Esplora Server**. Per impostazione predefinita, elenco nodi dispongono di un **Visualizza nel Browser** voce di menu contestuale che è possibile fare clic per aprire gli elenchi in un Web browser. In questo esempio estende i nodi di elenco aggiungendo un **vista in Visual Studio** voce di menu contestuale che consente di aprire elenchi direttamente in Visual Studio. Il codice accede ai dati dell'elenco per il nodo ottenere l'URL dell'elenco per aprire in Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 In questo esempio Usa il servizio di progetto SharePoint per ottenere il <xref:EnvDTE.DTE> oggetto che consente di aprire elenchi in Visual Studio. Per altre informazioni sul servizio di progetto SharePoint, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Per altre informazioni sulle attività di base per creare un'estensione per un nodo SharePoint, vedere [come: Estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuire l'estensione
 Per distribuire il **Esplora Server** estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura: Estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Distribuire le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
