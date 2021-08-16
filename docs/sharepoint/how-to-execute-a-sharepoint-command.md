---
title: 'Procedura: Eseguire un comando SharePoint comando | Microsoft Docs'
description: Leggere come creare un comando personalizzato SharePoint per chiamare l'API del modello a oggetti del server da un'estensione SharePoint tools.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 6f5ccf33e8b8262233282224eb01c9dc3c00f0c014e5b7cde35adb665b4384ab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121385237"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Procedura: Eseguire un comando SharePoint comando
  Se si vuole usare il modello a oggetti del server in un'estensione SharePoint tools, è necessario creare un comando SharePoint *personalizzato* per chiamare l'API. Dopo aver definito il comando e distribuirlo con l'estensione SharePoint tools, l'estensione può eseguire il comando per chiamare nel modello SharePoint a oggetti del server. Per eseguire il comando, usare uno dei metodi ExecuteCommand di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.

 Per altre informazioni sullo scopo dei comandi SharePoint, vedere Chiamare i SharePoint [a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Per eseguire un comando SharePoint

1. Nell'estensione SharePoint tools ottenere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto . Il modo in cui si <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> ottiene un oggetto dipende dal tipo di estensione che si sta creando:

    - In un'estensione del SharePoint progetto, usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> proprietà .

         Per altre informazioni sulle estensioni del sistema del progetto, vedere [Estendere il SharePoint del progetto.](../sharepoint/extending-the-sharepoint-project-system.md)

    - In un'estensione **del nodo SharePoint connections** in **Esplora server** usare la proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> . Per ottenere un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> oggetto , usare la proprietà <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> .

         Per altre informazioni sulle **estensioni Esplora server,** vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - Nel codice che non fa parte di un'estensione degli strumenti SharePoint, ad esempio una creazione guidata modello di progetto, usare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> proprietà .

         Per altre informazioni sul recupero del servizio di progetto, vedere [Usare il](../sharepoint/using-the-sharepoint-project-service.md)SharePoint servizio di progetto .

2. Chiamare uno dei metodi ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> dell'oggetto. Passare il nome del comando da eseguire al primo argomento del metodo ExecuteCommand. Se il comando ha un parametro personalizzato, passare tale parametro al secondo argomento del metodo ExecuteCommand.

     Esiste un overload ExecuteCommand diverso per ogni firma di comando supportata. Nella tabella seguente sono elencate le firme supportate e l'overload da usare per ogni firma.

    |Firma del comando|Overload ExecuteCommand da usare|
    |-----------------------|------------------------------------|
    |Il comando ha solo il parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predefinito e nessun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha solo il parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predefinito e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha due parametri (il parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predefinito e un parametro personalizzato) e nessun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha due parametri e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come usare l'overload per chiamare il comando descritto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> `Contoso.Commands.UpgradeSolution` in [Procedura: Creare](../sharepoint/how-to-create-a-sharepoint-command.md)un SharePoint comando .

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs" id="Snippet6":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb" id="Snippet6":::

 Il `Execute` metodo illustrato in questo esempio è un'implementazione del metodo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> dell'interfaccia in un passaggio di distribuzione personalizzato. Per visualizzare questo codice nel contesto di un esempio più ampio, vedere [Procedura dettagliata: Creare](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)un passaggio di distribuzione personalizzato per SharePoint progetti .

 Si notino i dettagli seguenti sulla chiamata al <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metodo :

- Il primo parametro identifica il comando che si vuole chiamare. Questa stringa corrisponde al valore passato a nella <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> definizione del comando.

- Il secondo parametro è il valore che si vuole passare al secondo parametro personalizzato del comando. In questo caso, è il percorso completo del file con estensione *wsp* che viene aggiornato al SharePoint sito.

- Il codice non passa il parametro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implicito al comando. Questo parametro viene passato automaticamente al comando quando si chiama il comando da un'estensione del sistema di progetto SharePoint o da un'estensione del nodo connessioni **SharePoint** in **Esplora server**. In altri tipi di soluzioni, ad esempio in una creazione guidata modello di progetto che implementa l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> , questo parametro è **Null.**

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un riferimento a Microsoft.VisualStudio. SharePoint assembly.

## <a name="see-also"></a>Vedi anche
- [Chiamare nei modelli SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Procedura: Creare un comando SharePoint comando](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
