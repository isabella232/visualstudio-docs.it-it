---
title: Ottenere dati per un nodo SharePoint incorporato in Esplora server
titleSuffix: ''
description: Recuperare i dati per il componente di SharePoint sottostante di un nodo SharePoint incorporato nella finestra di Esplora server di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c49f091477d204b7ed81a6f89fb24a56b2d60669
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945110"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Procedura: ottenere dati per un nodo SharePoint incorporato in Esplora server
  Per ogni nodo SharePoint incorporato in **Esplora server**, è possibile recuperare i dati per il componente di SharePoint sottostante rappresentato dal nodo. Per ulteriori informazioni, vedere [estensione del nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come ottenere i dati per l'elenco di SharePoint sottostante rappresentato da un nodo elenco in **Esplora server**. Per impostazione predefinita, i nodi elenco hanno una **visualizzazione nella** voce del menu di scelta rapida del browser su cui è possibile fare clic per aprire gli elenchi in un Web browser. Questo esempio consente di estendere i nodi dell'elenco aggiungendo una visualizzazione nella voce del menu di scelta rapida di **Visual Studio** che apre gli elenchi direttamente in Visual Studio. Il codice accede ai dati dell'elenco per il nodo per ottenere l'URL dell'elenco da aprire in Visual Studio.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 In questo esempio viene utilizzato il servizio di progetto SharePoint per ottenere l' <xref:EnvDTE.DTE> oggetto utilizzato per aprire gli elenchi in Visual Studio. Per ulteriori informazioni sul servizio di progetto SharePoint, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Per ulteriori informazioni sulle attività di base per creare un'estensione per un nodo di SharePoint, vedere [procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- EnvDTE

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione **Esplora server** , creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
