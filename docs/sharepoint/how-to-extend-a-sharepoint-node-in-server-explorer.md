---
title: 'Procedura: Estendere un nodo SharePoint in Esplora Server | Microsoft Docs'
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
ms.openlocfilehash: c5e617b57437033f4194d96647ebff9d1c4e2c2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813997"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Procedura: Estendere un nodo SharePoint in Esplora Server
  È possibile estendere i nodi sotto il **connessioni di SharePoint** nodo **Esplora Server**. Ciò è utile quando si desidera aggiungere nuovi nodi figlio, voci di menu di scelta rapida o le proprietà a un nodo esistente. Per altre informazioni, vedere [estendere del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Per estendere un nodo SharePoint in Esplora Server

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft.VisualStudio.SharePoint.Explorer.Extensions

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente a Visual Studio di individuare e caricare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al costruttore dell'attributo.

5. Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe. Questo attributo specifica l'identificatore di stringa per il tipo di nodo che si vuole estendere.

     Per specificare i tipi di nodo predefiniti forniti da Visual Studio, passare uno dei seguenti valori di enumerazione al costruttore dell'attributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Usare questi valori per specificare i nodi di connessione del sito (i nodi che consentono di visualizzare gli URL dei siti), i nodi, o tutti gli altri nodi padre nel sito **Esplora Server**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Usare questi valori per specificare uno dei nodi predefiniti che rappresentano un singolo componente in un sito di SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.

6. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metodo, utilizzare i membri del *nodeType* parametro per aggiungere funzionalità al nodo. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> oggetto che fornisce accesso agli eventi definiti nel <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaccia. Ad esempio, è possibile gestire gli eventi seguenti:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Gestire questo evento per aggiungere nuovi nodi figlio al nodo. Per altre informazioni, vedere [Procedura: Aggiungere un nodo personalizzato di SharePoint a Esplora Server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Gestire questo evento per aggiungere una voce di menu di scelta rapida personalizzati al nodo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Gestire questo evento per aggiungere proprietà personalizzate al nodo. Le proprietà vengono visualizzate nel **proprietà** finestra quando si seleziona il nodo.

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come creare due diversi tipi di nodo estensioni:

- Un'estensione che consente di aggiungere un menu di scelta rapida per i nodi del sito SharePoint. Quando si sceglie la voce di menu, viene visualizzato il nome del nodo in cui è stato fatto clic.

- Un'estensione che aggiunge una proprietà personalizzata denominata **ContosoExampleProperty** a ogni nodo che rappresenta un campo denominato **corpo**.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Questa estensione aggiunge una proprietà stringa modificabile per i nodi. È anche possibile creare proprietà personalizzate che consentono di visualizzare i dati di sola lettura dal server SharePoint. Per un esempio che illustra come eseguire questa operazione, vedere [procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>Distribuire l'estensione
 Per distribuire il **Esplora Server** estensione, creare un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) creare un pacchetto per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Aggiungere un nodo personalizzato di SharePoint a Esplora Server](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Associare dati personalizzati con le estensioni degli strumenti di SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
