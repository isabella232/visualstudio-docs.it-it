---
title: Estensione degli strumenti di SharePoint in Visual Studio | Microsoft Docs
description: Estendere gli strumenti di SharePoint in Visual Studio. Estendere il sistema del progetto SharePoint. Estendere il nodo connessioni di SharePoint in Esplora server.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a921f45ea151ce7ee3313dba47e81a5acc86063d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672626"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Estendere gli strumenti di SharePoint in Visual Studio
  Gli strumenti di SharePoint in Visual Studio soddisfano i requisiti di molti scenari di sviluppo di applicazioni. Tuttavia, è possibile individuare i casi in cui non forniscono funzionalità richieste dall'utente o da altri sviluppatori. In questi casi, è possibile estendere gli strumenti di SharePoint per creare le funzionalità necessarie.

## <a name="how-to-extend-the-sharepoint-tools"></a>Come estendere gli strumenti di SharePoint
 È possibile estendere il sistema del progetto SharePoint e il nodo **connessioni di SharePoint** nella finestra di **Esplora server** .

### <a name="extend-the-sharepoint-project-system"></a>Estendere il sistema del progetto SharePoint
 Visual Studio include un set di modelli di progetto e modelli di elementi che è possibile usare per creare soluzioni SharePoint. Ad esempio, sono disponibili modelli per i ricevitori di eventi, le definizioni di elenco, i flussi di lavoro e Web part. Tuttavia, è anche possibile definire tipi personalizzati di elementi di progetto SharePoint per la creazione di componenti di SharePoint, ad esempio campi o azioni personalizzate. È inoltre possibile creare estensioni per i tipi di elementi di progetto SharePoint già installati in Visual Studio ed è possibile creare estensioni per i progetti SharePoint.

 Per ulteriori informazioni, vedere [estensione del sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Estendere il nodo connessioni di SharePoint in Esplora server
 In Visual Studio è possibile usare il nodo **connessioni di SharePoint** nella finestra di **Esplora server** per visualizzare molti dei componenti di uno o più siti SharePoint locali in una visualizzazione struttura ad albero gerarchica. È inoltre possibile estendere il nodo **connessioni di SharePoint** nei modi seguenti:

- Aggiungendo nodi personalizzati. Questa opzione è utile se si desidera visualizzare i componenti dei siti di SharePoint che non sono visualizzati per impostazione predefinita.

- Estendendo i nodi esistenti. Ad esempio, è possibile aggiungere un nuovo nodo figlio a un nodo esistente oppure è possibile aggiungere una voce di menu di scelta rapida a un nodo ed eseguire attività quando uno sviluppatore fa clic sulla voce di menu.

  Per ulteriori informazioni, vedere [estensione del nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Requisiti del computer di sviluppo
 Per creare estensioni per gli strumenti di SharePoint, il computer di sviluppo deve soddisfare gli stessi requisiti per la creazione di soluzioni SharePoint in Visual Studio.

 Si consiglia inoltre di installare il [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . L'SDK include i modelli di progetto e gli strumenti che è possibile usare per estendere Visual Studio. In particolare, l'SDK include un modello di progetto che è possibile usare per creare facilmente un pacchetto di estensione di Visual Studio (VSIX). I pacchetti VSIX rappresentano il modo migliore per distribuire le estensioni di Visual Studio in Visual Studio. Tutte le estensioni degli strumenti di SharePoint devono essere distribuite usando pacchetti VSIX. Per tutte le procedure dettagliate di questa documentazione si presuppone che sia [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] installato.

 Per installare Visual Studio SDK, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Per altre informazioni sulle estensioni di Visual Studio, vedere [avvio dello sviluppo di estensioni di Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica del modello di programmazione delle estensioni degli strumenti di SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Estendere il sistema del progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Estendere il nodo connessioni di SharePoint in Esplora server](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Programmazione di concetti e funzionalità per le estensioni degli strumenti di SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Riferimento &#40;estensibilità degli strumenti di SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Estensioni di debug per gli strumenti di SharePoint in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Distribuire estensioni per gli strumenti di SharePoint in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)