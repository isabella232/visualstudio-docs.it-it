---
title: 'Procedura: Eseguire un comando di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: db95754fd27820e0686f65a22393f51510467fb6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631185"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Procedura: Eseguire un comando di SharePoint
  Se si desidera utilizzare il modello a oggetti server in un'estensione degli strumenti di SharePoint, è necessario creare una classe personalizzata *comando SharePoint* per chiamare l'API. Dopo aver definito il comando e distribuirlo con l'estensione strumenti di SharePoint, l'estensione può eseguire il comando per effettuare chiamate nel modello a oggetti server SharePoint. Per eseguire il comando, usare uno dei metodi di ExecuteCommand un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.

 Per altre informazioni sullo scopo dei comandi di SharePoint, vedere [chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Per eseguire un comando di SharePoint

1.  Nell'estensione strumenti di SharePoint, ottenere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto. Il modo in cui ottenere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto dipende dal tipo di estensione che si sta creando:

    -   In un'estensione del sistema del progetto SharePoint, utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> proprietà.

         Per altre informazioni sulle estensioni del sistema di progetto, vedere [estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    -   In un'estensione del **connessioni di SharePoint** nodo **Esplora Server**, usare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> proprietà. Per ottenere un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> dell'oggetto, usare il <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> proprietà.

         Per altre informazioni sulle **Esplora Server** estensioni, vedere [estendere del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    -   Nel codice che non fa parte di un'estensione degli strumenti di SharePoint, ad esempio la creazione guidata modello di progetto, usare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> proprietà.

         Per altre informazioni sul recupero del servizio di progetto, vedere [usare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2.  Chiamare uno dei metodi ExecuteCommand del <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto. Passare il nome del comando da eseguire per il primo argomento del metodo ExecuteCommand. Se il comando ha un parametro personalizzato, passare tale parametro per il secondo argomento del metodo ExecuteCommand.

     È disponibile un altro overload ExecuteCommand per ogni firma comando supportati. La tabella seguente elenca le supportati firme e overload da utilizzare per ogni firma.

    |Firma del comando|ExecuteCommand overload da usare|
    |-----------------------|------------------------------------|
    |Il comando ha solo il valore predefinito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro e restituisce alcun valore.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha solo il valore predefinito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha due parametri (il valore predefinito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro e un parametro personalizzato) e restituisce alcun valore.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha due parametri e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Esempio
 Esempio di codice seguente viene illustrato come utilizzare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> overload per chiamare il `Contoso.Commands.UpgradeSolution` comando descritto in [come: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 Il `Execute` metodo illustrato in questo esempio è un'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metodo il <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaccia in un passaggio di distribuzione personalizzato. Per informazioni su questo codice nel contesto di un esempio più esaustivo, vedere [procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Notare i seguenti dettagli relativi alla chiamata al <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> metodo:

-   Il primo parametro identifica il comando che si desidera chiamare. Questa stringa corrisponde al valore passato al <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> sulla definizione dei comandi.

-   Il secondo parametro è il valore che si desidera passare al secondo parametro del comando personalizzato. In questo caso, è il percorso completo del *wsp* file che viene aggiornato al sito di SharePoint.

-   Il codice non supera implicito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro al comando. Questo parametro viene passato al comando automaticamente quando si chiama il comando da un'estensione del sistema del progetto SharePoint o un'estensione del **connessioni di SharePoint** nodo **Server Explorer**. In altri tipi di soluzioni, ad esempio la creazione guidata modello di progetto che implementa il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia, questo parametro è **null**.

## <a name="compile-the-code"></a>Compilare il codice
 In questo esempio richiede un riferimento all'assembly Microsoft.VisualStudio.SharePoint.

## <a name="see-also"></a>Vedere anche
- [Chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Procedura: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
