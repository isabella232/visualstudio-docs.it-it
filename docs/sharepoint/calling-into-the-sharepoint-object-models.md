---
title: La chiamata ai modelli a oggetti di SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd6e8d1bbd2f880a3e3c4c7fab4b292a2c7bd6d0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875667"
---
# <a name="call-into-the-sharepoint-object-models"></a>Chiamare i modelli a oggetti SharePoint
  Quando si creano estensioni per gli strumenti di SharePoint in Visual Studio, è necessario chiamare APIs di SharePoint per eseguire determinate attività. Ad esempio, se si crea un passaggio di distribuzione personalizzato per progetti SharePoint, potrebbe essere necessario chiamare APIs per eseguire alcune attività per distribuire soluzioni di SharePoint.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] forniscono due modelli a oggetti diversi che è possibile usare nelle estensioni di strumenti di SharePoint: un modello a oggetti server e un modello a oggetti client. Ogni modello a oggetti presenta vantaggi e svantaggi nel contesto delle estensioni di strumenti di SharePoint.  
  
 Per una panoramica dei modelli a oggetti di SharePoint, vedere [estensioni degli strumenti Panoramica del modello di programmazione di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>Usare il modello a oggetti client nei progetti di estensione
 Quando si sviluppa un'estensione per gli strumenti di SharePoint, è possibile usare il modello a oggetti client nel progetto, come qualsiasi altro set di API gestite. È possibile aggiungere riferimenti agli assembly nel modello a oggetti client al progetto ed è possibile chiamare le API nel modello a oggetti client direttamente dal codice.  
  
 Tuttavia, il modello a oggetti client presenta due svantaggi nel contesto delle estensioni di strumenti di SharePoint:  
  
- Il modello a oggetti client fornisce solo un subset del modello a oggetti server. Se è necessario usare le funzionalità di SharePoint che non sono esposta nel modello a oggetti client, è necessario usare il modello a oggetti server.  
  
- Usando il modello a oggetti client nelle estensioni di strumenti di SharePoint deve funzionare nella maggior parte dei casi, si potrebbero verificarsi alcuni scenari in cui le chiamate al modello a oggetti client non funzionano come previsto. Il modello a oggetti client è progettato per essere utilizzato nelle applicazioni client per effettuare chiamate nei siti di SharePoint su un server remoto o una farm. Gli strumenti di SharePoint in Visual Studio funzionano solo con un'installazione di SharePoint locale nel computer di sviluppo. Pertanto, quando si usa il modello a oggetti client in un'estensione degli strumenti di SharePoint, chiamare in un sito di SharePoint nel computer locale, ovvero non modo in cui il modello a oggetti client è stato progettato per essere utilizzato.  
  
  Per una procedura dettagliata che illustra come usare il modello a oggetti client in un'estensione degli strumenti di SharePoint in Visual Studio, vedere [procedura dettagliata: Chiamare il modello a oggetti client SharePoint in un'estensione di Esplora Server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>Usare il modello a oggetti server nei progetti di estensione
 Il modello a oggetti server è un superset del modello a oggetti client. Quando si usa il modello a oggetti server, è possibile usare tutte le funzionalità che [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] espongono a livello di codice.  

 Le estensioni degli strumenti di SharePoint possono usare le API nel modello a oggetti server, ma non possono chiamare direttamente le API. Il modello a oggetti server può essere chiamato solo da un processo a 64 bit destinato a .NET Framework 3.5. Tuttavia, le estensioni degli strumenti di SharePoint richiedono il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e vengono eseguiti nel processo di Visual Studio a 32 bit. Ciò impedisce che le estensioni degli strumenti di SharePoint che fa riferimento l'assembly nel modello a oggetti server SharePoint direttamente.  
  
 Se si desidera utilizzare il modello a oggetti server in un'estensione degli strumenti di SharePoint, è necessario creare una classe personalizzata *comando SharePoint* per chiamare l'API. Definire il comando di SharePoint in un assembly secondario che può chiamare direttamente nel modello a oggetti server. Nel progetto di estensione, viene chiamato il comando di SharePoint indirettamente tramite il metodo ExecuteCommand di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.  
  
 Per altre informazioni sulla creazione e utilizzo dei comandi di SharePoint, vedere [come: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) e [come: Eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Per informazioni su come distribuire i comandi di SharePoint, vedere [distribuisce le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Per esercitazioni dettagliate che illustrano come creare e usare i comandi di SharePoint, vedere [procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) e [procedura dettagliata: Estendere Esplora Server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>Comprendere come vengono eseguiti i comandi di SharePoint
 Gli assembly che definiscono i comandi di SharePoint vengono caricati in un processo host a 64 bit denominato *vssphost4.exe*. Dopo aver chiamato un comando di SharePoint in un'estensione degli strumenti di SharePoint, il comando viene eseguito dal *vssphost4.exe* anziché al processo di Visual Studio a 32 bit (*devenv.exe*). È possibile controllare alcuni aspetti del modo in cui i comandi di SharePoint vengono eseguiti impostando i valori del Registro di sistema. Per altre informazioni, vedere [eseguire il Debug delle estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Procedura: Eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Estensioni degli strumenti Panoramica del modello di programmazione di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
