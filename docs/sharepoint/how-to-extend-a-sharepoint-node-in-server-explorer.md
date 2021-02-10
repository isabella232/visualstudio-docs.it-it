---
title: 'Procedura: estendere un nodo SharePoint in Esplora server | Microsoft Docs'
description: Informazioni su come estendere un nodo SharePoint in Esplora server usando il nodo connessioni di SharePoint.
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
ms.openlocfilehash: 4983930a7c16edef826a5912abf0870598b1f906
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943796"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Procedura: estendere un nodo SharePoint in Esplora server
  È possibile estendere i nodi nel nodo **connessioni di SharePoint** in **Esplora server**. Questa opzione è utile quando si desidera aggiungere nuovi nodi figlio, voci di menu di scelta rapida o proprietà a un nodo esistente. Per ulteriori informazioni, vedere [estensione del nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Per estendere un nodo SharePoint in Esplora server

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente a Visual Studio di individuare e caricare l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al costruttore dell'attributo.

5. Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe. Questo attributo specifica l'identificatore di stringa per il tipo di nodo che si desidera estendere.

     Per specificare i tipi di nodo incorporati forniti da Visual Studio, passare uno dei seguenti valori di enumerazione al costruttore dell'attributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Usare questi valori per specificare i nodi di connessione del sito (i nodi che visualizzano gli URL del sito), i nodi del sito o tutti gli altri nodi padre in **Esplora server**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Usare questi valori per specificare uno dei nodi predefiniti che rappresentano un singolo componente in un sito di SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.

6. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metodo usare i membri del parametro *NodeType* per aggiungere funzionalità al nodo. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> oggetto che fornisce l'accesso agli eventi definiti nell' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaccia. Ad esempio, è possibile gestire gli eventi seguenti:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Gestire questo evento per aggiungere nuovi nodi figlio al nodo. Per altre informazioni, vedere [procedura: aggiungere un nodo SharePoint personalizzato a Esplora server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Gestire questo evento per aggiungere una voce di menu di scelta rapida personalizzata al nodo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Gestire questo evento per aggiungere proprietà personalizzate al nodo. Le proprietà vengono visualizzate nella finestra **Proprietà** quando si seleziona il nodo.

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come creare due tipi diversi di estensioni di nodo:

- Estensione che aggiunge una voce di menu di scelta rapida ai nodi del sito di SharePoint. Quando si fa clic sulla voce di menu, viene visualizzato il nome del nodo su cui è stato fatto clic.

- Estensione che aggiunge una proprietà personalizzata denominata **ContosoExampleProperty** a ogni nodo che rappresenta un campo denominato **Body**.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Questa estensione aggiunge una proprietà di stringa modificabile ai nodi. È inoltre possibile creare proprietà personalizzate che visualizzano i dati di sola lettura dal server SharePoint. Per un esempio in cui viene illustrato come eseguire questa operazione, vedere [procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione **Esplora server** , creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: aggiungere un nodo SharePoint personalizzato a Esplora server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Associare dati personalizzati alle estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
