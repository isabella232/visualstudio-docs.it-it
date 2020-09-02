---
title: Chiamata ai modelli a oggetti di SharePoint | Microsoft Docs
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
ms.openlocfilehash: 24634143a40f7b163c0b658bddb5596041868033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62988402"
---
# <a name="call-into-the-sharepoint-object-models"></a>Chiamare nei modelli a oggetti di SharePoint
  Quando si creano estensioni per gli strumenti di SharePoint in Visual Studio, potrebbe essere necessario chiamare le API di SharePoint per eseguire determinate attività. Se, ad esempio, si crea una fase di distribuzione personalizzata per i progetti SharePoint, potrebbe essere necessario chiamare le API di SharePoint per eseguire alcune delle attività per distribuire le soluzioni.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] forniscono due modelli a oggetti diversi che è possibile usare nelle estensioni degli strumenti di SharePoint: un modello a oggetti del server e un modello a oggetti del client. Ogni modello a oggetti presenta vantaggi e svantaggi nel contesto delle estensioni degli strumenti di SharePoint.

 Per una panoramica dei modelli a oggetti di SharePoint, vedere [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Usare il modello a oggetti del client nei progetti di estensione
 Quando si sviluppa un'estensione per gli strumenti di SharePoint, è possibile usare il modello a oggetti del client nel progetto come qualsiasi altro set di API gestite. È possibile aggiungere al progetto riferimenti agli assembly nel modello a oggetti del client ed è possibile chiamare le API nel modello a oggetti del client direttamente dal codice.

 Tuttavia, il modello a oggetti del client presenta due svantaggi nel contesto delle estensioni degli strumenti di SharePoint:

- Il modello a oggetti del client fornisce solo un subset del modello a oggetti del server. Se è necessario utilizzare le funzionalità di SharePoint non esposte nel modello a oggetti del client, è necessario utilizzare il modello a oggetti del server.

- Sebbene l'utilizzo del modello a oggetti del client nelle estensioni degli strumenti di SharePoint funzioni nella maggior parte dei casi, è possibile che si verifichino alcuni scenari in cui le chiamate al modello a oggetti del client non funzionano come previsto. Il modello a oggetti del client è progettato per essere utilizzato nelle applicazioni client per chiamare i siti di SharePoint in un server o una farm remota. Gli strumenti di SharePoint in Visual Studio funzionano solo con un'installazione di SharePoint locale nel computer di sviluppo. Pertanto, quando si utilizza il modello a oggetti del client in un'estensione degli strumenti di SharePoint, si effettua una chiamata in un sito di SharePoint nel computer locale, che non è il modo in cui il modello a oggetti del client è stato progettato per essere utilizzato.

  Per una procedura dettagliata in cui viene illustrato come utilizzare il modello a oggetti del client in un'estensione degli strumenti di SharePoint in Visual Studio, vedere [procedura dettagliata: effettuare una chiamata nel modello a oggetti del client di SharePoint in un'estensione Esplora server](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Usare il modello a oggetti del server nei progetti di estensione
 Il modello a oggetti del server è un superset del modello a oggetti del client. Quando si utilizza il modello a oggetti del server, è possibile utilizzare tutte le funzionalità esposte [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ed [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] esporre a livello di codice.

 Le estensioni degli strumenti di SharePoint possono usare le API nel modello a oggetti del server, ma non possono chiamare direttamente le API. Il modello a oggetti del server può essere chiamato solo da un processo a 64 bit destinato a .NET Framework 3,5. Tuttavia, le estensioni degli strumenti di SharePoint richiedono [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e vengono eseguite nel processo di Visual Studio a 32 bit. In questo modo si impedisce che le estensioni degli strumenti di SharePoint facciano riferimento direttamente agli assembly nel modello a oggetti del server SharePoint.

 Se si desidera utilizzare il modello a oggetti del server in un'estensione degli strumenti di SharePoint, è necessario creare un *comando di SharePoint* personalizzato per chiamare l'API. Il comando di SharePoint viene definito in un assembly secondario che può chiamare direttamente il modello a oggetti del server. Nel progetto di estensione, il comando di SharePoint viene chiamato indirettamente tramite il metodo ExecuteCommand di un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> oggetto.

 Per altre informazioni sulla creazione e sull'uso dei comandi di SharePoint, vedere [procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) e [procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Per informazioni su come distribuire i comandi di SharePoint, vedere la pagina relativa alla [distribuzione di estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Per le procedure dettagliate che illustrano come creare e utilizzare i comandi di SharePoint, vedere [procedura dettagliata: creazione di un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) e [procedura dettagliata: estendere Esplora server per visualizzare le web part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Informazioni sul modo in cui vengono eseguiti i comandi di SharePoint
 Gli assembly che definiscono i comandi di SharePoint vengono caricati in un processo host a 64 bit denominato *vssphost4.exe*. Dopo aver chiamato un comando di SharePoint in un'estensione degli strumenti di SharePoint, il comando viene eseguito da *vssphost4.exe* al posto del processo di Visual Studio a 32 bit (*devenv.exe*). È possibile controllare alcuni aspetti della modalità di esecuzione dei comandi di SharePoint impostando i valori nel registro di sistema. Per altre informazioni, vedere [estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: creare un comando di SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Procedura: eseguire un comando di SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
