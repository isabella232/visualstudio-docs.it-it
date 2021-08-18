---
title: 'Procedura: Aggiungere o rimuovere SharePoint connessioni | Microsoft Docs'
description: Aggiungere o rimuovere SharePoint connessioni usando il nodo SharePoint Connessioni nella finestra Esplora server di Visual Studio.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136079"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Procedura: Aggiungere o rimuovere SharePoint connessioni
  Esplora server consente di esplorare SharePoint siti e connessioni dati. Tuttavia, prima di poter esplorare il contenuto di un SharePoint è necessario aggiungerlo al nodo SharePoint **Connessioni.**

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Per aggiungere un SharePoint al nodo SharePoint connessioni

1. Sulla barra dei menu scegliere **Visualizza**, **quindi Esplora server**.

2. In **Esplora server** scegliere il nodo SharePoint **Connessioni** e quindi, sulla barra dei menu, scegliere Strumenti Aggiungi SharePoint  >  **connessione**.

3. Nella casella **Aggiungi SharePoint connessione** immettere per il sito SharePoint [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] (ad esempio, http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Per eliminare un SharePoint dal nodo SharePoint connessioni

1. Sulla barra dei menu scegliere **Visualizza**, quindi **Esplora server** per aprire **Esplora server**.

2. Espandere il **nodo SharePoint connessioni** per visualizzare il SharePoint da eliminare da **Esplora server**.

3. Scegliere il sito e quindi sulla barra dei menu scegliere **Modifica**  >  **Elimina.**

    > [!NOTE]
    > Questo passaggio non elimina il sito sottostante. elimina solo la connessione da **Esplora server**.

## <a name="see-also"></a>Vedi anche
- [Esplorare SharePoint connessioni con Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
