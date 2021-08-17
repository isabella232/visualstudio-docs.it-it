---
title: Estensione degli strumenti SharePoint in Visual Studio | Microsoft Docs
description: Estendere gli strumenti SharePoint in Visual Studio. Estendere il SharePoint di progetto. Estendere il nodo SharePoint connessioni in Esplora server.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 31165f4d3f9b70fe9848163c8a3771cc8e886e1f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027188"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Estendere gli strumenti SharePoint in Visual Studio
  Gli SharePoint in Visual Studio soddisfano i requisiti di molti scenari di sviluppo di applicazioni. Tuttavia, è possibile individuare casi in cui non forniscono funzionalità richieste dall'utente o da altri sviluppatori. In questi casi, è possibile estendere gli SharePoint per creare le funzionalità necessarie.

## <a name="how-to-extend-the-sharepoint-tools"></a>Come estendere gli strumenti SharePoint
 È possibile estendere il SharePoint di progetto e **il SharePoint connessioni** nella finestra **Esplora server.**

### <a name="extend-the-sharepoint-project-system"></a>Estendere il SharePoint del progetto
 Visual Studio include un set di modelli di progetto e modelli di elemento che è possibile usare per creare SharePoint soluzioni. Ad esempio, sono disponibili modelli per ricevitori di eventi, definizioni di elenco, flussi di lavoro e Web part. Tuttavia, è anche possibile definire tipi personalizzati di elementi SharePoint progetto per la creazione SharePoint componenti quali campi o azioni personalizzate. È anche possibile creare estensioni per SharePoint tipi di elemento di progetto già installati in Visual Studio ed è possibile creare estensioni per SharePoint progetti.

 Per altre informazioni, vedere [Estendere il SharePoint del progetto.](../sharepoint/extending-the-sharepoint-project-system.md)

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Estendere il nodo SharePoint connessioni in Esplora server
 In Visual Studio è possibile usare il nodo Connessioni **SharePoint** nella finestra **di Esplora server** per visualizzare molti dei componenti di uno o più siti SharePoint locali in una visualizzazione albero gerarchica. È anche possibile estendere il **SharePoint connessioni di** rete nei modi seguenti:

- Aggiungendo i propri nodi. Ciò è utile se si desidera visualizzare i componenti SharePoint siti che non vengono visualizzati per impostazione predefinita.

- Estendendo i nodi esistenti. Ad esempio, è possibile aggiungere un nuovo nodo figlio a un nodo esistente oppure aggiungere una voce di menu di scelta rapida a un nodo ed eseguire attività quando uno sviluppatore fa clic sulla voce di menu.

  Per altre informazioni, vedere [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Requisiti del computer di sviluppo
 Per creare estensioni per gli strumenti SharePoint, il computer di sviluppo deve soddisfare gli stessi requisiti per la creazione SharePoint soluzioni in Visual Studio.

 È anche consigliabile installare [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . L'SDK include modelli di progetto e strumenti che è possibile usare per estendere Visual Studio. In particolare, l'SDK include un modello di progetto che è possibile usare per creare facilmente un pacchetto Visual Studio Extension (VSIX). I pacchetti VSIX sono il modo migliore per distribuire Visual Studio estensioni in Visual Studio. Tutte SharePoint strumenti di distribuzione devono essere distribuite tramite pacchetti VSIX. Tutte le procedure dettagliate in questa documentazione presuppongono che sia [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installato .

 Per installare Visual Studio SDK, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md) Per altre informazioni sulle Visual Studio, vedere [Starting to Develop Visual Studio Extensions](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Vedi anche

- [Panoramica del modello di programmazione delle estensioni SharePoint strumenti](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Estendere il SharePoint del progetto](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estendere il nodo SharePoint connessioni in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Concetti e funzionalità di programmazione per le estensioni SharePoint tools](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Informazioni di &#40;SharePoint strumenti di estendibilità&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Eseguire il debug delle estensioni per SharePoint strumenti in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Distribuire estensioni per gli strumenti SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)