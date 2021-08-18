---
title: Chiamata al SharePoint a oggetti | Microsoft Docs
description: Informazioni su come chiamare nei due diversi modelli a oggetti che è possibile usare nelle estensioni SharePoint strumenti.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0cdcee9a763a7354ceca6821796f455a1a878aa3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100452"
---
# <a name="call-into-the-sharepoint-object-models"></a>Chiamare nei modelli SharePoint a oggetti
  Quando si creano estensioni per gli strumenti SharePoint in Visual Studio, potrebbe essere necessario chiamare SharePoint API per eseguire determinate attività. Ad esempio, se si crea un passaggio di distribuzione personalizzato per i progetti SharePoint, potrebbe essere necessario chiamare le API SharePoint per eseguire alcune delle attività per distribuire soluzioni.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]e forniscono due diversi modelli a oggetti che è possibile usare nelle estensioni SharePoint strumenti: un modello a oggetti [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] server e un modello a oggetti client. Ogni modello a oggetti presenta vantaggi e svantaggi nel contesto delle estensioni SharePoint strumenti.

 Per una panoramica dei modelli SharePoint a oggetti, vedere Panoramica del modello di programmazione [delle estensioni SharePoint tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Usare il modello a oggetti client nei progetti di estensione
 Quando si sviluppa un'estensione per gli SharePoint, è possibile usare il modello a oggetti client nel progetto come qualsiasi altro set di API gestite. È possibile aggiungere riferimenti agli assembly nel modello a oggetti client al progetto ed è possibile chiamare le API nel modello a oggetti client direttamente dal codice.

 Tuttavia, il modello a oggetti client presenta due svantaggi nel contesto delle estensioni SharePoint strumenti:

- Il modello a oggetti client fornisce solo un subset del modello a oggetti del server. Se è necessario usare una SharePoint non esposta nel modello a oggetti client, è necessario usare il modello a oggetti del server.

- Anche se l'uso del modello SharePoint a oggetti client nelle estensioni degli strumenti di SharePoint dovrebbe funzionare nella maggior parte dei casi, è possibile che si verifichino alcuni scenari in cui le chiamate al modello a oggetti client non funzionano come previsto. Il modello a oggetti client è progettato per essere usato nelle applicazioni client per chiamare in SharePoint in un server remoto o in una farm. Gli SharePoint in Visual Studio funzionano solo con un'SharePoint locale nel computer di sviluppo. Pertanto, quando si usa il modello a oggetti client in un'estensione degli strumenti SharePoint, si chiama in un sito SharePoint nel computer locale, che non è il modo in cui il modello a oggetti client è stato progettato per l'uso.

  Per una procedura dettagliata che illustra come usare il modello a oggetti client in un'estensione degli strumenti SharePoint in Visual Studio, vedere [Procedura dettagliata:](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)Chiamare il modello a oggetti client SharePoint in un'estensione Esplora server .

## <a name="use-the-server-object-model-in-extension-projects"></a>Usare il modello a oggetti del server nei progetti di estensione
 Il modello a oggetti del server è un superset del modello a oggetti client. Quando si usa il modello a oggetti del server, è possibile usare tutte le funzionalità che [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ed [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] espongono a livello di codice.

 SharePoint estensioni degli strumenti di configurazione possono usare le API nel modello a oggetti del server, ma non possono chiamare direttamente le API. Il modello a oggetti del server può essere chiamato solo da un processo a 64 bit destinato .NET Framework 3.5. Tuttavia, SharePoint estensioni degli strumenti richiedono e vengono eseguite nel processo di Visual Studio [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a 32 bit. In questo modo SharePoint estensioni degli strumenti non fanno riferimento direttamente agli assembly nel SharePoint a oggetti del server.

 Se si vuole usare il modello a oggetti del server in un'estensione SharePoint tools, è necessario creare un comando SharePoint *personalizzato* per chiamare l'API. Si definisce il SharePoint comando in un assembly secondario che può chiamare direttamente nel modello a oggetti del server. Nel progetto di estensione si chiama il comando SharePoint indirettamente usando il metodo ExecuteCommand di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.

 Per altre informazioni sulla creazione e sull'SharePoint comandi, vedere [Procedura: Creare](../sharepoint/how-to-create-a-sharepoint-command.md) un comando SharePoint e [Procedura:](../sharepoint/how-to-execute-a-sharepoint-command.md)Eseguire un comando SharePoint . Per informazioni su come distribuire SharePoint comandi, vedere Distribuire estensioni per gli strumenti SharePoint [in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Per le procedure dettagliate che illustrano come creare e usare i comandi SharePoint, vedere Procedura [dettagliata:](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) Creare un passaggio di distribuzione personalizzato per i progetti SharePoint e Procedura dettagliata: estendere Esplora server per visualizzare [le web part.](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

### <a name="understand-how-sharepoint-commands-are-executed"></a>Informazioni sulla modalità SharePoint comandi
 Gli assembly che definiscono SharePoint comandi vengono caricati in un processo host a 64 bit denominato *vssphost4.exe*. Dopo aver chiamato un comando SharePoint in un'estensione degli strumenti SharePoint, il comando viene eseguito da *vssphost4.exe* anziché dal processo Visual Studio a 32 bit (*devenv.exe*). È possibile controllare alcuni aspetti del modo in cui SharePoint comandi vengono eseguiti impostando i valori nel Registro di sistema. Per altre informazioni, vedere [Eseguire il debug delle estensioni per SharePoint strumenti in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Procedura: Creare un comando SharePoint comando](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Procedura: Eseguire un comando SharePoint comando](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Panoramica del modello di programmazione delle estensioni SharePoint tools](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
