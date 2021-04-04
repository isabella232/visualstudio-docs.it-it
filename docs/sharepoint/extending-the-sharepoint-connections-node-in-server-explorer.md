---
title: Estensione del nodo connessioni di SharePoint in Esplora server | Microsoft Docs
titleSuffix: ''
description: Estendere il nodo connessioni di SharePoint nella finestra Esplora server in Visual Studio. Aggiungere proprietà personalizzate ai nodi. Ottenere i dati per i nodi predefiniti.
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
ms.workload:
- office
ms.openlocfilehash: 1f77e0044b8ae3c7456a31bb9c9153ba9e9f4c99
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218035"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Estendere il nodo connessioni di SharePoint in Esplora server
  In Visual Studio è possibile connettersi ai siti di SharePoint locali nel computer di sviluppo usando il nodo **connessioni di SharePoint** nella finestra **Esplora server** . In questo nodo vengono visualizzati molti dei componenti dei siti di SharePoint locali in una visualizzazione struttura ad albero gerarchica. Ad esempio, è possibile visualizzare gli elenchi, le raccolte documenti e i tipi di contenuto nei siti locali. Per ulteriori informazioni sull'utilizzo di **Esplora server** per connettersi ai siti di SharePoint locali, vedere [Browse SharePoint connections using Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 È possibile estendere il nodo **connessioni di SharePoint** creando estensioni per i nodi esistenti oppure creando un tipo di nodo personalizzato e aggiungendolo alla gerarchia dei nodi.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Attività per l'estensione del nodo connessioni di SharePoint
 Per estendere un nodo esistente, creare un'estensione di Visual Studio che implementi l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Quando si estende un nodo, è possibile aggiungere funzionalità al nodo, ad esempio voci di menu di scelta rapida o proprietà personalizzate. Per altre informazioni, vedere [procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Per creare un tipo di nodo personalizzato, creare un'estensione di Visual Studio che implementi l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Creare un nodo personalizzato se si desidera visualizzare i componenti dei siti di SharePoint che non sono visualizzati in **Esplora server** per impostazione predefinita. Ad esempio, **Esplora server** non Visualizza la raccolta web part di un sito di SharePoint per impostazione predefinita, ma è possibile aggiungere un nodo personalizzato che esegue questa operazione. Per altre informazioni, vedere [procedura: aggiungere un nodo SharePoint personalizzato a Esplora server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) e [procedura dettagliata: estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Aggiungere proprietà personalizzate ai nodi
 Quando si estende un nodo o si crea un tipo di nodo personalizzato, è possibile aggiungere proprietà personalizzate al nodo. Le proprietà vengono visualizzate nella finestra **Proprietà** quando si seleziona il nodo.

 Esistono due tipi di proprietà personalizzate che è possibile aggiungere a un nodo:

- Proprietà che visualizzano un set di dati di sola lettura dal sito di SharePoint. I dati descrivono il componente di SharePoint rappresentato dal nodo. Per una procedura dettagliata che illustra come eseguire questa operazione, vedere [procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Proprietà che visualizzano i dati personalizzati di lettura/scrittura. Per un esempio di codice che illustra come eseguire questa operazione, vedere [procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Ottenere i dati per i nodi predefiniti
 Tutti i nodi predefiniti forniti da Visual Studio includono alcuni dati sul componente di SharePoint che rappresentano. Un nodo che rappresenta un elenco nel sito di SharePoint, ad esempio, fornisce alcuni dati relativi all'elenco, ad esempio il titolo e l'URL della visualizzazione predefinita per l'elenco.

 Per accedere a questi dati, recuperare un oggetto dati dalla <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà dell' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto che rappresenta il nodo a cui si è interessati. Il tipo di oggetto dati dipende dal tipo del nodo.

 Nell'esempio di codice riportato di seguito viene illustrato come ottenere l'oggetto dati per un nodo elenco. Per vedere questo esempio nel contesto di un esempio più ampio, vedere [procedura: ottenere dati per un nodo SharePoint incorporato in Esplora server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet11":::

 Nella tabella seguente sono elencati i tipi di oggetto dati per ogni tipo di nodo incorporato.

|Tipo di nodo|Tipo di oggetto dati|
|---------------|----------------------|
|Nodo sito di SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Tipo di contenuto|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Funzionalità|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|Elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Modello di elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Visualizzazione elenco (Microsoft. SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Associazione del flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Modello di flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Per altre informazioni sull'uso della <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà, vedere [associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procedura: aggiungere un nodo SharePoint personalizzato a Esplora server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Procedura: ottenere dati per un nodo SharePoint incorporato in Esplora server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Esplorazione delle connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
