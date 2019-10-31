---
title: 'Procedura: creare un comando di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c07d541dc4f68f33d48e7cb41b6bc3923b2ea52
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189236"
---
# <a name="how-to-create-a-sharepoint-command"></a>Procedura: creare un comando di SharePoint
  Se si desidera utilizzare il modello a oggetti del server in un'estensione degli strumenti di SharePoint, è necessario creare un *comando di SharePoint* personalizzato per chiamare l'API. Il comando di SharePoint viene definito in un assembly che può chiamare direttamente nel modello a oggetti del server.

 Per ulteriori informazioni sullo scopo dei comandi di SharePoint, vedere la pagina relativa alla [chiamata nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Per creare un comando di SharePoint

1. Creare un progetto libreria di classi con la seguente configurazione:

    - Ha come destinazione il .NET Framework 3,5. Per ulteriori informazioni sulla selezione del Framework di destinazione, vedere [How to: target a version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Ha come destinazione la piattaforma AnyCPU o x64. Per impostazione predefinita, la piattaforma di destinazione per i progetti di libreria di classi è AnyCPU. Per altre informazioni sulla selezione della piattaforma di destinazione, vedere [procedura: configurare progetti per piattaforme di destinazione](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Non è possibile implementare un comando di SharePoint nello stesso progetto che definisce un'estensione degli strumenti di SharePoint, perché i comandi di SharePoint hanno come destinazione le estensioni .NET Framework 3,5 e gli strumenti di SharePoint destinate al [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. È necessario definire tutti i comandi di SharePoint utilizzati dall'estensione in un progetto distinto. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft. VisualStudio. SharePoint. Commands

    - Microsoft. SharePoint

3. In una classe del progetto, creare un metodo che definisce il comando di SharePoint. Il metodo deve essere conforme alle linee guida seguenti:

    - Può avere uno o due parametri.

         Il primo parametro deve essere un oggetto <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>. Questo oggetto fornisce Microsoft. SharePoint. SPSite o Microsoft. SharePoint. SPWeb in cui viene eseguito il comando. Fornisce anche un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> oggetto che può essere usato per scrivere messaggi nella finestra di **output** o **Elenco errori** finestra in Visual Studio.

         Il secondo parametro può essere un tipo di propria scelta, ma questo parametro è facoltativo. È possibile aggiungere questo parametro al comando di SharePoint se è necessario passare i dati dall'estensione degli strumenti di SharePoint al comando.

    - Può avere un valore restituito, ma è facoltativo.

    - Il secondo parametro e il valore restituito devono essere un tipo che può essere serializzato dal Windows Communication Foundation (WCF). Per ulteriori informazioni, vedere [tipi supportati dal serializzatore dei contratti dati](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) e [utilizzo della classe XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Il metodo può avere qualsiasi visibilità (**public**, **Internal**o **private**) e può essere static o non static.

4. Applicare il <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> al metodo. Questo attributo specifica un identificatore univoco per il comando. Questo identificatore non deve corrispondere al nome del metodo.

     Quando si chiama il comando dall'estensione degli strumenti di SharePoint, è necessario specificare lo stesso identificatore univoco. Per altre informazioni, vedere [procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Esempio
 Nell'esempio di codice riportato di seguito viene illustrato un comando di SharePoint con l'identificatore `Contoso.Commands.UpgradeSolution`. Questo comando usa le API nel modello a oggetti del server per eseguire l'aggiornamento a una soluzione distribuita.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Oltre al primo parametro implicito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>, questo comando include anche un parametro di stringa personalizzato che contiene il percorso completo del file con estensione wsp aggiornato al sito di SharePoint. Per visualizzare questo codice nel contesto di un esempio più ampio, vedere [procedura dettagliata: creare un passaggio di distribuzione personalizzato per i progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Compilazione del codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft. VisualStudio. SharePoint. Commands

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Distribuzione del comando
 Per distribuire il comando, includere l'assembly del comando nello stesso pacchetto di estensione [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (*VSIX*) con l'assembly dell'estensione che usa il comando. È inoltre necessario aggiungere una voce per l'assembly dei comandi nel file Extension. vsixmanifest. Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Chiamare nei modelli a oggetti di SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
