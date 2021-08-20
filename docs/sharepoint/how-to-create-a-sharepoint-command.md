---
title: 'Procedura: Creare un SharePoint comando | Microsoft Docs'
description: Informazioni su come creare un comando SharePoint personalizzato per chiamare l'API del modello a oggetti del server in un'estensione SharePoint strumenti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: caaca2226b80a1e1aef4246094a01c158b8e2951
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136053"
---
# <a name="how-to-create-a-sharepoint-command"></a>Procedura: Creare un comando SharePoint comando
  Se si vuole usare il modello a oggetti del server in un'estensione degli strumenti SharePoint, è necessario creare un comando SharePoint *personalizzato* per chiamare l'API. Si definisce il SharePoint comando in un assembly che può chiamare direttamente nel modello a oggetti del server.

 Per altre informazioni sullo scopo dei comandi SharePoint, vedere [Chiamare i SharePoint a oggetti.](../sharepoint/calling-into-the-sharepoint-object-models.md)

### <a name="to-create-a-sharepoint-command"></a>Per creare un comando SharePoint

1. Creare un progetto libreria di classi con la configurazione seguente:

    - La destinazione è .NET Framework 3.5. Per altre informazioni sulla selezione del framework di destinazione, [vedere Procedura: Impostare come](../ide/visual-studio-multi-targeting-overview.md)destinazione una versione del .NET Framework .

    - È destinato alla piattaforma AnyCPU o x64. Per impostazione predefinita, la piattaforma di destinazione per i progetti di libreria di classi è AnyCPU. Per altre informazioni sulla selezione della piattaforma di destinazione, vedere [Procedura: Configurare progetti per piattaforme di destinazione.](../ide/how-to-configure-projects-to-target-platforms.md)

    > [!NOTE]
    > Non è possibile implementare un comando SharePoint nello stesso progetto che definisce un'estensione degli strumenti SharePoint, perché i comandi SharePoint hanno come destinazione le estensioni degli strumenti .NET Framework 3.5 e SharePoint per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . È necessario definire tutti SharePoint comandi usati dall'estensione in un progetto separato. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint. Comandi

    - Microsoft. SharePoint

3. In una classe del progetto creare un metodo che definisce il SharePoint comando. Il metodo deve essere conforme alle linee guida seguenti:

    - Può avere uno o due parametri.

         Il primo parametro deve essere un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> oggetto . Questo oggetto fornisce Microsoft. SharePoint. SPSite o Microsoft. SharePoint. SPWeb in cui viene eseguito il comando. Fornisce inoltre un oggetto che può essere usato per scrivere messaggi nella finestra Output o nella <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> **finestra Elenco** errori in Visual Studio. 

         Il secondo parametro può essere un tipo a scelta, ma questo parametro è facoltativo. È possibile aggiungere questo parametro al comando SharePoint se è necessario passare dati dall'estensione SharePoint tools al comando .

    - Può avere un valore restituito, ma questo è facoltativo.

    - Il secondo parametro e il valore restituito devono essere un tipo che può essere serializzato da Windows Communication Foundation (WCF). Per altre informazioni, vedere [Tipi supportati dal serializzatore del contratto](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) dati e Uso della classe [XmlSerializer.](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)

    - Il metodo può avere qualsiasi visibilità (**public**, **internal** o **private)** e può essere statico o non statico.

4. Applicare <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> l'oggetto al metodo . Questo attributo specifica un identificatore univoco per il comando. Questo identificatore non deve corrispondere al nome del metodo.

     È necessario specificare lo stesso identificatore univoco quando si chiama il comando dall'estensione SharePoint tools. Per altre informazioni, [vedere Procedura: Eseguire un comando SharePoint comando](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato SharePoint comando con l'identificatore `Contoso.Commands.UpgradeSolution` . Questo comando usa le API nel modello a oggetti del server per eseguire l'aggiornamento a una soluzione distribuita.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet5":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet5":::

 Oltre al primo parametro implicito, questo comando include anche un parametro stringa personalizzato che contiene il percorso completo del file con estensione wsp che viene aggiornato al <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> SharePoint sito. Per visualizzare questo codice nel contesto di un esempio più ampio, vedere [Procedura dettagliata: Creare un](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)passaggio di distribuzione personalizzato per SharePoint progetti .

## <a name="compiling-the-code"></a>Compilazione del codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint. Comandi

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Distribuzione del comando
 Per distribuire il comando, includere l'assembly del comando nello stesso pacchetto di estensione [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] (*vsix*) con l'assembly di estensione che usa il comando . È anche necessario aggiungere una voce per l'assembly del comando nel file extension.vsixmanifest. Per altre informazioni, vedere [Deploy extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Chiamare nei modelli SharePoint a oggetti](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Procedura: Eseguire un comando SharePoint comando](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Procedura dettagliata: Estendere Esplora server per visualizzare web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
