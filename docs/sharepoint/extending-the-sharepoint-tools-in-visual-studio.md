---
title: Estensione degli strumenti di SharePoint in Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4394c583d281f114392088ed6a346e05d084070e
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327307"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Estendere gli strumenti di SharePoint in Visual Studio
  Gli strumenti di SharePoint in Visual Studio soddisfano i requisiti di molti scenari di sviluppo di applicazioni. Tuttavia, è possibile individuare casi in cui non forniscono funzionalità che richiedono l'utente o altri sviluppatori. In questi casi, è possibile estendere gli strumenti di SharePoint per creare le funzionalità necessarie.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Come estendere gli strumenti di SharePoint
 È possibile estendere il sistema di progetto SharePoint e il **connessioni di SharePoint** nodo il **Esplora Server** finestra.  
  
### <a name="extend-the-sharepoint-project-system"></a>Estendere il sistema di progetto SharePoint
 Visual Studio include un set di modelli di progetto e modelli di elementi che è possibile usare per creare soluzioni di SharePoint. Ad esempio, sono disponibili modelli per i ricevitori di eventi, le definizioni di elenco, flussi di lavoro e Web part. Tuttavia, è anche possibile definire i propri tipi di elementi di progetto SharePoint per la creazione di componenti di SharePoint, ad esempio i campi o azioni personalizzate. È anche possibile creare estensioni per i tipi di elemento di progetto SharePoint che sono già installati in Visual Studio ed è possibile creare estensioni per i progetti SharePoint.  
  
 Per altre informazioni, vedere [estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Estensione del nodo Connessioni di SharePoint in Esplora Server
 In Visual Studio, è possibile usare la **connessioni di SharePoint** nodo il **Esplora Server** finestra per visualizzare molti dei componenti di uno o più siti SharePoint locali in una visualizzazione struttura ad albero gerarchica. È anche possibile estendere il **connessioni di SharePoint** nodo nei modi seguenti:  
  
-   Tramite l'aggiunta di nodi personalizzati. Ciò è utile se si desidera visualizzare i componenti di siti di SharePoint che non vengono visualizzati per impostazione predefinita.  
  
-   Estendendo i nodi esistenti. Ad esempio, è possibile aggiungere un nuovo nodo figlio a un nodo esistente oppure è possibile aggiungere una voce di menu di scelta rapida a un nodo ed eseguire attività quando uno sviluppatore fa clic sulla voce di menu.  
  
 Per altre informazioni, vedere [estendere del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Requisiti del computer di sviluppo
 Per creare estensioni per gli strumenti di SharePoint, il computer di sviluppo deve soddisfare gli stessi requisiti per la creazione di soluzioni SharePoint in Visual Studio. Per altre informazioni, vedere [i requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 È inoltre consigliabile installare la [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. il SDK include modelli di progetto e strumenti che è possibile usare per estendere Visual Studio. In particolare, il SDK include un modello di progetto che è possibile usare per creare facilmente un pacchetto di Visual Studio Extension (VSIX). I pacchetti VSIX sono il modo migliore per distribuire le estensioni di Visual Studio in Visual Studio. Tutte le estensioni di strumenti di SharePoint devono essere distribuite utilizzando pacchetti VSIX. Tutte le procedure dettagliate di questa documentazione si presuppone che il [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installato.  
  
 Per installare Visual Studio SDK, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Per altre informazioni sulle estensioni di Visual Studio, vedere [iniziando a sviluppare estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>Vedere anche
 [Estensioni degli strumenti Panoramica del modello di programmazione di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Estensione del nodo Connessioni di SharePoint in Esplora Server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Concetti di programmazione e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Riferimento &#40;estendibilità degli strumenti di SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Eseguire il debug delle estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Distribuire le estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
