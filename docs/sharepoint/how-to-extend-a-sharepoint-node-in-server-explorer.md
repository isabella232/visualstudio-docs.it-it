---
title: 'Procedura: Estendere un nodo SharePoint in Esplora server | Microsoft Docs'
description: Informazioni su come estendere un nodo SharePoint in Esplora server usando il SharePoint Connections.
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
ms.openlocfilehash: 8ae10e800473eccd347f5dc1398510255d5b7ee4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130975"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Procedura: Estendere un nodo SharePoint in Esplora server
  È possibile estendere i nodi nel **nodo SharePoint connessioni** in **Esplora server**. Ciò è utile quando si vogliono aggiungere nuovi nodi figlio, voci di menu di scelta rapida o proprietà a un nodo esistente. Per altre informazioni, vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Per estendere un nodo SharePoint in Esplora server

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio. SharePoint. Explorer.Extensions

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente Visual Studio individuare e caricare <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> l'implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al costruttore dell'attributo.

5. Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe. Questo attributo specifica l'identificatore di stringa per il tipo di nodo che si vuole estendere.

     Per specificare i tipi di nodo predefiniti forniti da Visual Studio, passare uno dei valori di enumerazione seguenti al costruttore dell'attributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: usare questi valori per specificare i nodi di connessione del sito (i nodi che visualizzano gli URL del sito), i nodi del sito o tutti gli altri nodi padre **in Esplora server**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: usare questi valori per specificare uno dei nodi predefiniti che rappresentano un singolo componente in un sito SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.

6. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metodo usare i membri del parametro *nodeType* per aggiungere funzionalità al nodo. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> oggetto che fornisce l'accesso agli eventi definiti <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> nell'interfaccia . Ad esempio, è possibile gestire gli eventi seguenti:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: gestire questo evento per aggiungere nuovi nodi figlio al nodo. Per altre informazioni, vedere [Procedura: Aggiungere un nodo](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)SharePoint personalizzato a Esplora server .

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: gestire questo evento per aggiungere una voce di menu di scelta rapida personalizzata al nodo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: gestire questo evento per aggiungere proprietà personalizzate al nodo. Le proprietà vengono visualizzate nella **finestra Proprietà** quando il nodo viene selezionato.

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra come creare due diversi tipi di estensioni di nodo:

- Estensione che aggiunge una voce di menu di scelta rapida SharePoint nodi del sito. Quando si fa clic sulla voce di menu, viene visualizzato il nome del nodo su cui è stato fatto clic.

- Estensione che aggiunge una proprietà personalizzata denominata **ContosoExampleProperty** a ogni nodo che rappresenta un campo denominato **Body.**

  :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs" id="Snippet9":::
  :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb" id="Snippet9":::

  Questa estensione aggiunge una proprietà stringa modificabile ai nodi. È anche possibile creare proprietà personalizzate che visualizzano dati di sola lettura dal server SharePoint server. Per un esempio che illustra come eseguire questa operazione, vedere Procedura dettagliata: estendere [Esplora server per visualizzare web part.](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- Microsoft.VisualStudio. SharePoint. Explorer.Extensions

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire **l'Esplora server,** creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che si [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere un nodo SharePoint personalizzato a Esplora server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Associare dati personalizzati alle estensioni SharePoint strumenti di configurazione](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
