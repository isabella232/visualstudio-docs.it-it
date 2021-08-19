---
title: Estensione del nodo SharePoint connessioni in Esplora server | Microsoft Docs
titleSuffix: ''
description: Estendere il nodo SharePoint connessioni nella finestra Esplora server in Visual Studio. Aggiungere proprietà personalizzate ai nodi. Ottenere i dati per i nodi predefiniti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c6ae20393f60ffe0e17cee9baf85c1572cea32ac
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060154"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Estendere il nodo SharePoint connessioni in Esplora server
  In Visual Studio, è possibile connettersi ai siti SharePoint locali nel computer  di sviluppo usando il nodo Connessioni SharePoint nella finestra **Esplora server.** Questo nodo visualizza molti dei componenti dei siti SharePoint in una visualizzazione albero gerarchica. Ad esempio, è possibile visualizzare gli elenchi, le raccolte documenti e i tipi di contenuto nei siti locali. Per altre informazioni **sull'Esplora server** per connettersi ai siti SharePoint locali, vedere Esplorare SharePoint [connessioni tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 È possibile estendere **il nodo SharePoint connections** creando estensioni per i nodi esistenti oppure creando un tipo di nodo personalizzato e aggiungendolo alla gerarchia dei nodi.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Attività per l'estensione del nodo SharePoint connessioni
 Per estendere un nodo esistente, creare un'estensione Visual Studio che implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> l'interfaccia . Quando si estende un nodo, è possibile aggiungere funzionalità al nodo, ad esempio voci di menu di scelta rapida personalizzate o proprietà personalizzate. Per altre informazioni, vedere [Procedura: Estendere un](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)nodo SharePoint in Esplora server .

 Per creare un tipo di nodo personalizzato, creare un'Visual Studio che implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> l'interfaccia . Creare un nodo personalizzato se si vogliono visualizzare i componenti SharePoint siti che non vengono visualizzati **Esplora server** per impostazione predefinita. Ad esempio, **Esplora server** la raccolta web part di un sito SharePoint per impostazione predefinita, ma è possibile aggiungere un nodo personalizzato che esegue questa operazione. Per altre informazioni, vedere [Procedura: Aggiungere](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) un nodo SharePoint personalizzato a Esplora server e [Procedura dettagliata:](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)Estendere Esplora server per visualizzare Web part .

## <a name="add-custom-properties-to-nodes"></a>Aggiungere proprietà personalizzate ai nodi
 Quando si estende un nodo o si crea un tipo di nodo personalizzato, è possibile aggiungere proprietà personalizzate al nodo. Le proprietà vengono visualizzate nella **finestra Proprietà** quando il nodo viene selezionato.

 Esistono due tipi di proprietà personalizzate che è possibile aggiungere a un nodo:

- Proprietà che visualizzano un set di dati di sola lettura dal SharePoint sito. I dati descrivono SharePoint componente che rappresenta il nodo. Per una procedura dettagliata che illustra come eseguire questa operazione, vedere [Procedura dettagliata: estendere Esplora server per visualizzare web part.](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- Proprietà che visualizzano dati di lettura/scrittura personalizzati. Per un esempio di codice che illustra come eseguire questa operazione, vedere [Procedura:](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)Estendere un nodo SharePoint in Esplora server .

## <a name="get-data-for-built-in-nodes"></a>Ottenere dati per i nodi predefiniti
 Tutti i nodi predefiniti forniti da Visual Studio includono alcuni dati sul componente SharePoint che rappresentano. Ad esempio, un nodo che rappresenta un elenco nel sito SharePoint fornisce alcuni dati sull'elenco, ad esempio il titolo e l'URL della visualizzazione predefinita per l'elenco.

 Per accedere a questi dati, recuperare un oggetto dati dalla <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> dell'oggetto che rappresenta il nodo a cui si è interessati. Il tipo dell'oggetto dati dipende dal tipo di nodo.

 Nell'esempio di codice seguente viene illustrato come ottenere l'oggetto dati per un nodo elenco. Per visualizzare questo esempio nel contesto di un esempio più ampio, vedere [Procedura: Ottenere](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)dati per un nodo SharePoint predefinito in Esplora server .

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet11":::

 Nella tabella seguente sono elencati i tipi di oggetto dati per ogni tipo di nodo predefinito.

|Tipo di nodo|Tipo di oggetto dati|
|---------------|----------------------|
|SharePoint del sito|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Tipo di contenuto|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Funzionalità|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Modello di elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Visualizzazione elenco (Microsoft.SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Associazione del flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Modello di flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Per altre informazioni sull'uso della proprietà , vedere Associare dati <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> personalizzati alle estensioni SharePoint [tools](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Procedura: Estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procedura: Aggiungere un nodo SharePoint personalizzato a Esplora server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Procedura: Ottenere dati per un nodo SharePoint in Esplora server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Associare dati personalizzati alle estensioni SharePoint strumenti di configurazione](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Esplorare SharePoint connessioni usando Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Estendere gli SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
