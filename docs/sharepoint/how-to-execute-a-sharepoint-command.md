---
title: 'Procedura: eseguire un comando di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 789b77f3161b5fe566ea033060e8cab16cbaecc7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016982"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Procedura: eseguire un comando di SharePoint
  Se si desidera utilizzare il modello a oggetti del server in un'estensione degli strumenti di SharePoint, è necessario creare un *comando di SharePoint* personalizzato per chiamare l'API. Dopo aver definito il comando e averlo distribuito con l'estensione degli strumenti di SharePoint, l'estensione può eseguire il comando per effettuare una chiamata nel modello a oggetti del server SharePoint. Per eseguire il comando, usare uno dei metodi ExecuteCommand di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.

 Per ulteriori informazioni sullo scopo dei comandi di SharePoint, vedere la pagina relativa alla [chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Per eseguire un comando di SharePoint

1. Nell'estensione degli strumenti di SharePoint ottenere un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto. Il modo in cui si ottiene un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto dipende dal tipo di estensione che si sta creando:

    - In un'estensione del sistema del progetto SharePoint, utilizzare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> Proprietà.

         Per ulteriori informazioni sulle estensioni del sistema di progetto, vedere [estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - In un'estensione del nodo **connessioni di SharePoint** in **Esplora server**, utilizzare la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> Proprietà. Per ottenere un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> oggetto, usare la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> Proprietà.

         Per ulteriori informazioni sulle estensioni **Esplora server** , vedere [estensione del nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - Nel codice che non fa parte di un'estensione degli strumenti di SharePoint, ad esempio la creazione guidata modello di progetto, utilizzare la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> Proprietà.

         Per ulteriori informazioni sul recupero del servizio del progetto, vedere [utilizzare il servizio di progetto SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Chiamare uno dei metodi ExecuteCommand dell' <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto. Passare il nome del comando che si desidera eseguire al primo argomento del metodo ExecuteCommand. Se il comando ha un parametro personalizzato, passare il parametro al secondo argomento del metodo ExecuteCommand.

     È disponibile un overload ExecuteCommand diverso per ogni firma del comando supportata. La tabella seguente elenca le firme supportate e l'overload da usare per ogni firma.

    |Firma del comando|Overload ExecuteCommand da usare|
    |-----------------------|------------------------------------|
    |Il comando ha solo il <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro predefinito e nessun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha solo il <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro predefinito e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha due parametri (il <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro predefinito e un parametro personalizzato) e nessun valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |Il comando ha due parametri e un valore restituito.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato come utilizzare l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Overload per chiamare il `Contoso.Commands.UpgradeSolution` comando descritto in [procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 Il `Execute` metodo illustrato in questo esempio è un'implementazione del <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> metodo dell' <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaccia in un passaggio di distribuzione personalizzato. Per visualizzare questo codice nel contesto di un esempio più ampio, vedere [procedura dettagliata: creare un passaggio di distribuzione personalizzato per i progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Si notino i dettagli seguenti sulla chiamata al <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> Metodo:

- Il primo parametro identifica il comando che si desidera chiamare. Questa stringa corrisponde al valore passato a <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> nella definizione del comando.

- Il secondo parametro è il valore che si desidera passare al secondo parametro personalizzato del comando. In questo caso, si tratta del percorso completo del file con *estensione wsp* aggiornato al sito di SharePoint.

- Il codice non passa il parametro implicito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> al comando. Questo parametro viene passato automaticamente al comando quando si chiama il comando da un'estensione del sistema del progetto SharePoint o da un'estensione del nodo **connessioni di SharePoint** in **Esplora server**. In altri tipi di soluzioni, ad esempio in una procedura guidata del modello di progetto che implementa l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia, questo parametro è **null**.

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede un riferimento all'assembly Microsoft. VisualStudio. SharePoint.

## <a name="see-also"></a>Vedere anche
- [Chiamare nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
