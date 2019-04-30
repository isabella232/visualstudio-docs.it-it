---
title: 'Procedura: Creare un comando di SharePoint | Microsoft Docs'
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
ms.openlocfilehash: d804acd19d585bf9517ce9b8d771290a1f1c214a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435461"
---
# <a name="how-to-create-a-sharepoint-command"></a>Procedura: Creare un comando di SharePoint
  Se si desidera utilizzare il modello a oggetti server in un'estensione degli strumenti di SharePoint, è necessario creare una classe personalizzata *comando SharePoint* per chiamare l'API. Il comando è definito in un assembly che è possibile chiamare direttamente nel modello a oggetti server.

 Per altre informazioni sullo scopo dei comandi di SharePoint, vedere [chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Per creare un comando di SharePoint

1. Creare un progetto di libreria di classi con la configurazione seguente:

    - È destinato a .NET Framework 3.5. Per altre informazioni sulla selezione del framework di destinazione, vedere [come: Scegliere una versione di .NET Framework di destinazione](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

    - Ha come destinazione il AnyCPU o x64 piattaforma. Per impostazione predefinita, la piattaforma di destinazione per i progetti libreria di classi è AnyCPU. Per altre informazioni sulla selezione della piattaforma di destinazione, vedere [come: Configurare progetti per le piattaforme di destinazione](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Non è possibile implementare un comando di SharePoint nello stesso progetto che definisce un'estensione degli strumenti di SharePoint, perché i comandi di SharePoint hanno come destinazione la destinazione di estensioni di strumenti .NET Framework 3.5 e SharePoint il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. È necessario definire i comandi di SharePoint che vengono utilizzati per l'estensione in un progetto separato. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. In una classe nel progetto, creare un metodo che definisce il comando di SharePoint. Il metodo deve essere conforme alle linee guida seguenti:

    - Può avere uno o due parametri.

         Il primo parametro deve essere un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> oggetto. Questo oggetto fornisce SPSite o SPWeb in cui viene eseguito il comando. Fornisce inoltre un' <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> oggetto che può essere utilizzato per scrivere i messaggi per il **Output** finestra o **elenco errori** finestra in Visual Studio.

         Il secondo parametro può essere un tipo di propria scelta, ma questo parametro è facoltativo. È possibile aggiungere questo parametro al comando di SharePoint se è necessario passare dati dall'estensione degli strumenti di SharePoint al comando.

    - Può avere un valore restituito, ma questa operazione è facoltativa.

    - Il secondo parametro e il valore restituito deve essere un tipo che può essere serializzato da Windows Communication Foundation (WCF). Per altre informazioni, vedere [tipi supportati dal serializzatore dei contratti dati](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) e [utilizzando la classe XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Il metodo può avere qualsiasi la visibilità (**pubbliche**, **interna**, o **private**), e può essere statico o non statici.

4. Applicare il <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> al metodo. Questo attributo specifica un identificatore univoco per il comando. Questo identificatore non deve corrispondere al nome di metodo.

     Quando si chiama il comando dall'estensione strumenti di SharePoint, è necessario specificare lo stesso identificatore univoco. Per altre informazioni, vedere [Procedura: Eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra un comando di SharePoint con l'identificatore `Contoso.Commands.UpgradeSolution`. Questo comando Usa le API nel modello a oggetti server per eseguire l'aggiornamento a una soluzione distribuita.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Oltre al primo implicito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametro, questo comando ha anche un parametro di stringa personalizzata che contiene il percorso completo del file con estensione wsp che viene aggiornato al sito di SharePoint. Per informazioni su questo codice nel contesto di un esempio più esaustivo, vedere [procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Compilazione del codice
 In questo esempio vengono richiesti riferimenti agli assembly seguenti:

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>Il comando di distribuzione
 Per distribuire il comando, includere il comando assembly nella stessa [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] estensione (*vsix*) pacchetto con l'assembly dell'estensione che usa il comando. È anche necessario aggiungere una voce per l'assembly del comando nel file Extension. vsixmanifest. Per altre informazioni, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Chiamare i modelli a oggetti SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Procedura: Eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
