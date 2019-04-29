---
title: Estensione del nodo Connessioni di SharePoint in Esplora Server | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b1d461419497a0a45f50f12589cf3ac978a7666
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967357"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Estensione del nodo Connessioni di SharePoint in Esplora Server
  In Visual Studio, è possibile connettersi ai siti SharePoint locali nel computer di sviluppo utilizzando la **connessioni di SharePoint** nodo il **Esplora Server** finestra. Questo nodo visualizza molti componenti dei siti di SharePoint locale in una visualizzazione struttura ad albero gerarchica. Ad esempio, è possibile visualizzare l'elenchi, raccolte documenti e i tipi di contenuto nei siti locali. Per altre informazioni sull'uso **Esplora Server** per connettersi ai siti di SharePoint locali, vedere [connessioni Sfoglia SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 È possibile estendere il **connessioni di SharePoint** nodo mediante la creazione di estensioni per i nodi esistenti o creando un tipo di nodo personalizzato e aggiungerlo alla gerarchia di nodi.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Attività per l'estensione del nodo Connessioni di SharePoint
 Per estendere un nodo esistente, creare un'estensione di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia. Quando si estende un nodo, è possibile aggiungere funzionalità al nodo, ad esempio il proprio voci di menu di scelta rapida o le proprietà personalizzate. Per altre informazioni, vedere [Procedura: Estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Per creare un tipo di nodo personalizzati, creare un'estensione di Visual Studio che implementa il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaccia. Creare un nodo personalizzato se si desidera visualizzare i componenti di siti di SharePoint che non vengono visualizzati nella **Esplora Server** per impostazione predefinita. Ad esempio, **Esplora Server** viene non visualizzato della raccolta Web Part di un sito di SharePoint per impostazione predefinita, ma è possibile aggiungere un nodo personalizzato che esegue questa operazione. Per altre informazioni, vedere [Procedura: Aggiungere un nodo personalizzato di SharePoint a Esplora Server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) e [procedura dettagliata: Estendere Esplora Server per visualizzare le Web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Aggiungere proprietà personalizzate ai nodi
 Quando un nodo di estensione o creare un tipo di nodo personalizzati, è possibile aggiungere proprietà personalizzate al nodo. Le proprietà vengono visualizzate nel **proprietà** finestra quando si seleziona il nodo.

 Esistono due tipi di proprietà personalizzate, che è possibile aggiungere a un nodo:

- Proprietà che consentono di visualizzare un set di dati di sola lettura dal sito di SharePoint. I dati descrivono il componente di SharePoint che rappresenta il nodo. Per una procedura dettagliata che illustra come eseguire questa operazione, vedere [procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Proprietà che consentono di visualizzare i dati di lettura/scrittura personalizzati. Per un esempio di codice che illustra come eseguire questa operazione, vedere [come: Estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Ottenere i dati per i nodi incorporati
 Tutti i nodi predefiniti forniti da Visual Studio includono alcuni dati relativi al componente di SharePoint che rappresentano. Ad esempio, un nodo che rappresenta un elenco nel sito di SharePoint fornisce alcuni dati sull'elenco, ad esempio il titolo e l'URL della visualizzazione predefinita per un elenco.

 Per accedere a questi dati, recuperare un oggetto dati dal <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> oggetto che rappresenta il nodo si è interessati. Il tipo dell'oggetto dati dipende dal tipo del nodo.

 Esempio di codice seguente viene illustrato come ottenere l'oggetto dati per un nodo di elenco. Per questo esempio nel contesto di un esempio più esaustivo, vedere [come: Ottenere i dati per un nodo SharePoint incorporato in Esplora Server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]

 Nella tabella seguente elenca i tipi di oggetto dati per ogni tipo di nodo predefiniti.

|Tipo di nodo|Tipo di oggetto dati|
|---------------|----------------------|
|Nodo del sito di SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Tipo di contenuto|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Funzionalità|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Modello di elenco|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Visualizzazione elenco (SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Associazione del flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Modello di flusso di lavoro|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Per altre informazioni sull'uso di <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> proprietà, vedere [estensioni degli strumenti di associazione dati personalizzati con SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Procedura: Estendere un nodo SharePoint in Esplora Server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procedura: Aggiungere un nodo personalizzato di SharePoint a Esplora Server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Procedura: Ottenere i dati per un nodo SharePoint incorporato in Esplora Server](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Esplorare le connessioni di SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Estendere gli strumenti di SharePoint in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
