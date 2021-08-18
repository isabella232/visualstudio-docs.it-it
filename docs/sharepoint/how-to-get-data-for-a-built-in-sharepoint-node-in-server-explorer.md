---
title: Ottenere i dati per il nodo SharePoint in Esplora server
titleSuffix: ''
description: Ottenere i dati per il SharePoint sottostante di un nodo SharePoint nella finestra Esplora server di Visual Studio.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 322a5278ab2b21b02fb501523bfe9663948ae0fe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026928"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Procedura: Ottenere dati per un nodo SharePoint in Esplora server
  Per ogni nodo SharePoint in **Esplora server**, è possibile ottenere i dati per il componente SharePoint sottostante rappresentato dal nodo. Per altre informazioni, vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come ottenere i dati per l'SharePoint sottostante rappresentato da un nodo elenco in **Esplora server**. Per impostazione predefinita, i nodi elenco hanno una **voce di** menu di scelta rapida Visualizza nel browser su cui è possibile fare clic per aprire gli elenchi in un Web browser. Questo esempio estende i nodi elenco aggiungendo una voce di menu **Visual Studio** menu di scelta rapida Visualizza che apre gli elenchi direttamente in Visual Studio. Il codice accede ai dati dell'elenco per il nodo per ottenere l'URL dell'elenco da aprire in Visual Studio.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet10":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet10":::

 In questo esempio viene SharePoint servizio di progetto per ottenere l'oggetto utilizzato per aprire <xref:EnvDTE.DTE> gli elenchi in Visual Studio. Per altre informazioni sul SharePoint servizio di progetto, vedere [Usare il](../sharepoint/using-the-sharepoint-project-service.md)SharePoint servizio di progetto .

 Per altre informazioni sulle attività di base per creare un'estensione per un nodo SharePoint, vedere [Procedura:](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)Estendere un nodo SharePoint in Esplora server .

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- EnvDTE

- Microsoft.VisualStudio. SharePoint

- Microsoft.VisualStudio. SharePoint. Explorer.Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire **l'Esplora server,** creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che si [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura: Estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md)
- [Distribuire estensioni per gli strumenti SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
