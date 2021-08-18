---
title: 'Procedura: Aggiungere un nodo SharePoint personalizzato a Esplora server | Microsoft Docs'
titleSuffix: ''
description: Aggiungere un nodo SharePoint personalizzato per Esplora server in Visual Studio. Visualizzare componenti SharePoint aggiuntivi che non vengono visualizzati in Esplora server per impostazione predefinita.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 73dac3ba52b31efd55a1c6621b0e32d098bdb997
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131157"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Procedura: Aggiungere un nodo SharePoint personalizzato a Esplora server
  È possibile aggiungere nodi personalizzati nel nodo **SharePoint connessioni** in **Esplora server**. Ciò è utile quando si vogliono visualizzare componenti aggiuntivi SharePoint che non vengono visualizzati **in** Esplora server per impostazione predefinita. Per altre informazioni, vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Per aggiungere un nodo personalizzato, creare prima di tutto una classe che definisce il nuovo nodo. Creare quindi un'estensione che aggiunge il nodo come figlio di un nodo esistente.

### <a name="to-define-the-new-node"></a>Per definire il nuovo nodo

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint

    - Microsoft.VisualStudio. SharePoint. Explorer.Extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.

4. Aggiungere gli attributi seguenti alla classe :

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Questo attributo consente Visual Studio individuare e caricare <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> l'implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> tipo al costruttore dell'attributo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. In una definizione di nodo questo attributo specifica l'identificatore di stringa per il nuovo nodo. È consigliabile usare il formato nome *società*. *nome del nodo* per assicurarsi che tutti i nodi abbia un identificatore univoco.

5. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> metodo usare i membri del parametro *typeDefinition* per configurare il comportamento del nuovo nodo. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> oggetto che fornisce l'accesso agli eventi definiti <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> nell'interfaccia .

     Nell'esempio di codice seguente viene illustrato come definire un nuovo nodo. Questo esempio presuppone che il progetto contenga un'icona denominata CustomChildNodeIcon come risorsa incorporata.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet6":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet6":::

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Per aggiungere il nuovo nodo come figlio di un nodo esistente

1. Nello stesso progetto della definizione del nodo creare una classe che implementa <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> l'interfaccia .

2. Aggiungere l'attributo <xref:System.ComponentModel.Composition.ExportAttribute> alla classe. Questo attributo consente Visual Studio individuare e caricare <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> l'implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al costruttore dell'attributo.

3. Aggiungere l'attributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> alla classe. In un'estensione di nodo questo attributo specifica l'identificatore di stringa per il tipo di nodo che si vuole estendere.

     Per specificare i tipi di nodo predefiniti forniti da Visual Studio, passare uno dei valori di enumerazione seguenti al costruttore dell'attributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: usare questi valori per specificare i nodi di connessione del sito (i nodi che visualizzano gli URL del sito), i nodi del sito o tutti gli altri nodi padre in **Esplora server**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: usare questi valori per specificare uno dei nodi predefiniti che rappresentano un singolo componente in un sito SharePoint, ad esempio un nodo che rappresenta un elenco, un campo o un tipo di contenuto.

4. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> metodo gestire <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> l'evento del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parametro .

5. Nel gestore eventi aggiungere il nuovo nodo alla raccolta di nodi figlio <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> dell'oggetto esposto dal parametro degli argomenti <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> dell'evento.

     Nell'esempio di codice seguente viene illustrato come aggiungere il nuovo nodo come figlio del nodo SharePoint del sito in **Esplora server**.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet7":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet7":::

## <a name="complete-example"></a>Esempio completo
 Nell'esempio di codice seguente viene fornito il codice completo per definire un nodo semplice e aggiungerlo come figlio del nodo del sito SharePoint in **Esplora server**.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs" id="Snippet5":::

## <a name="compiling-the-code"></a>Compilazione del codice
 Questo esempio presuppone che il progetto contenga un'icona denominata CustomChildNodeIcon come risorsa incorporata. Questo esempio richiede anche riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire **l'Esplora server,** creare un pacchetto di estensione (VSIX) per l'assembly e tutti gli altri file che si [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] desidera distribuire con l'estensione. Per altre informazioni, vedere [Deploy extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procedura: Estendere un nodo SharePoint in Esplora server](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
