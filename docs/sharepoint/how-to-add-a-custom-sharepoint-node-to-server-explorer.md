---
title: 'Procedura: aggiungere un nodo SharePoint personalizzato a Esplora server | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a74c9c879df57a5ff6444626870ee9f021fb4e9
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584885"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Procedura: aggiungere un nodo SharePoint personalizzato a Esplora server
  È possibile aggiungere nodi personalizzati nel nodo **connessioni di SharePoint** in **Esplora server**. Questa opzione è utile quando si desidera visualizzare componenti aggiuntivi di SharePoint che non vengono visualizzati in **Esplora server** per impostazione predefinita. Per ulteriori informazioni, vedere [estensione del nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Per aggiungere un nodo personalizzato, creare prima di tutto una classe che definisce il nuovo nodo. Creare quindi un'estensione che aggiunge il nodo come figlio di un nodo esistente.

### <a name="to-define-the-new-node"></a>Per definire il nuovo nodo

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.

4. Aggiungere gli attributi seguenti alla classe:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente a Visual Studio di individuare e caricare l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> tipo al costruttore dell'attributo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. In una definizione di nodo, questo attributo specifica l'identificatore di stringa per il nuovo nodo. Si consiglia di utilizzare il formato *nome società*. *nome del nodo* per assicurarsi che tutti i nodi abbiano un identificatore univoco.

5. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metodo usare i membri del parametro *typeDefinition* per configurare il comportamento del nuovo nodo. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> oggetto che fornisce l'accesso agli eventi definiti nell' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaccia.

     Nell'esempio di codice riportato di seguito viene illustrato come definire un nuovo nodo. Questo esempio presuppone che il progetto contenga un'icona denominata CustomChildNodeIcon come risorsa incorporata.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Per aggiungere il nuovo nodo come figlio di un nodo esistente

1. Nello stesso progetto della definizione del nodo, creare una classe che implementi l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaccia.

2. Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente a Visual Studio di individuare e caricare l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al costruttore dell'attributo.

3. Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe. In un'estensione del nodo, questo attributo specifica l'identificatore di stringa per il tipo di nodo che si desidera estendere.

     Per specificare i tipi di nodo incorporati forniti da Visual Studio, passare uno dei seguenti valori di enumerazione al costruttore dell'attributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Usare questi valori per specificare i nodi di connessione del sito (i nodi che visualizzano gli URL del sito), i nodi del sito o tutti gli altri nodi padre in **Esplora server**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Usare questi valori per specificare uno dei nodi predefiniti che rappresentano un singolo componente in un sito di SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.

4. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metodo, gestire l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> evento del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametro.

5. Nel <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> gestore eventi aggiungere il nuovo nodo alla raccolta di nodi figlio dell' <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> oggetto esposto dal parametro degli argomenti dell'evento.

     Nell'esempio di codice riportato di seguito viene illustrato come aggiungere il nuovo nodo come figlio del nodo del sito di SharePoint in **Esplora server**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Esempio completo
 Nell'esempio di codice riportato di seguito viene fornito il codice completo per definire un nodo semplice e aggiungerlo come figlio del nodo del sito di SharePoint in **Esplora server**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Compilazione del codice
 Questo esempio presuppone che il progetto contenga un'icona denominata CustomChildNodeIcon come risorsa incorporata. Questo esempio richiede anche riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione **Esplora server** , creare un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che si desidera distribuire con l'estensione. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura: estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
