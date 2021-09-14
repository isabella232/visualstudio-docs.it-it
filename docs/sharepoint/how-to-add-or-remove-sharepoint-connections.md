---
title: 'Procedura: Aggiungere o rimuovere connessioni SharePoint connessioni | Microsoft Docs'
description: Aggiungere o rimuovere SharePoint connessioni usando il nodo Connessioni SharePoint nella finestra Esplora server di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 90923440dcbe5201c30a1b8c97d1275cd9719f1c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625079"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Procedura: Aggiungere o rimuovere connessioni SharePoint rete
  Esplora server consente di esplorare SharePoint e le connessioni dati. Tuttavia, prima di poter esplorare il contenuto di un SharePoint, è necessario aggiungerlo al nodo SharePoint **connessioni.**

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Per aggiungere un sito SharePoint al nodo SharePoint connessioni

1. Sulla barra dei menu scegliere **Visualizza** **Esplora server**.

2. In **Esplora server** scegliere il nodo **Connessioni** SharePoint e quindi scegliere Strumenti Aggiungi SharePoint  >  **connessione**.

3. Nella casella **Add SharePoint Connection** (Aggiungi connessione di SharePoint) immettere per il sito di SharePoint [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] (ad esempio, http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Per eliminare un sito SharePoint dal nodo SharePoint connessioni

1. Sulla barra dei menu scegliere **Visualizza** **Esplora server** per aprire **Esplora server**.

2. Espandere il **SharePoint Connessioni** di rete per visualizzare il SharePoint che si vuole eliminare **da Esplora server**.

3. Scegliere il sito e quindi scegliere Modifica Elimina sulla barra  >  **dei** menu.

    > [!NOTE]
    > Questo passaggio non elimina il sito sottostante. elimina solo la connessione da **Esplora server**.

## <a name="see-also"></a>Vedi anche
- [Esplorare SharePoint connessioni usando Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
