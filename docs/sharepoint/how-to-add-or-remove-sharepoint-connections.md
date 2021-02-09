---
title: 'Procedura: aggiungere o rimuovere connessioni di SharePoint | Microsoft Docs'
description: Aggiungere o rimuovere connessioni di SharePoint utilizzando il nodo connessioni di SharePoint nella finestra di Esplora server di Visual Studio.
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
ms.workload:
- office
ms.openlocfilehash: 57ff132274ba7f720a845078b0424fe235d9c31e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923452"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Procedura: aggiungere o rimuovere connessioni di SharePoint
  Esplora server consente di esplorare i siti di SharePoint e le connessioni dati. Tuttavia, prima di poter esplorare il contenuto di un sito di SharePoint, è necessario aggiungerlo al nodo **connessioni di SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Per aggiungere un sito di SharePoint al nodo connessioni di SharePoint

1. Sulla barra dei menu scegliere **Visualizza**, **Esplora server**.

2. In **Esplora server** scegliere il nodo **connessioni di SharePoint** , quindi nella barra dei menu scegliere **strumenti**  >  **Aggiungi connessione SharePoint**.

3. Nella casella **Aggiungi connessione SharePoint** immettere [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il sito di SharePoint, ad esempio http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Per eliminare un sito di SharePoint dal nodo connessioni di SharePoint

1. Sulla barra dei menu scegliere **Visualizza**, **Esplora server** per aprire **Esplora server**.

2. Espandere il nodo **connessioni di SharePoint** per visualizzare il sito di SharePoint che si desidera eliminare dall' **Esplora server**.

3. Scegliere il sito, quindi nella barra dei menu scegliere **modifica**  >  **Elimina**.

    > [!NOTE]
    > Questo passaggio non elimina il sito sottostante; Elimina solo la connessione dal **Esplora server**.

## <a name="see-also"></a>Vedi anche
- [Esplorazione delle connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
