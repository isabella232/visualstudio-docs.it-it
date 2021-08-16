---
title: Aggiungere nodi dei risultati della ricerca nel set di schemi
description: Informazioni su come aggiungere nodi evidenziati in XML Schema Explorer come risultato di una ricerca di parole chiave nell'area di lavoro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: e9ab42d35aef489c18a12c3c738655dde1ccb9e971bf0caaf87513582645a79f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351005"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: Aggiungere nodi dei risultati della ricerca del set di schemi all'area di lavoro

Questo argomento illustra come aggiungere nodi evidenziati in **XML Schema Explorer** come risultato di una ricerca di parole chiave nell'area di lavoro.

> [!NOTE]
> Solo i nodi globali possono essere aggiunti all'area [di lavoro](../xml-tools/xml-schema-designer-workspace.md).

In questo esempio viene utilizzato lo [schema dell'ordine di acquisto di esempio](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi

1. Seguire la procedura descritta in [Procedura: Creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Digitare "purchaseOrder" nella casella di testo di ricerca della barra degli [strumenti di XML Explorer](../xml-tools/xml-schema-explorer.md) e fare clic sul pulsante di ricerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     I risultati della ricerca sono evidenziati in **XML Schema Explorer** e contrassegnati da segni di graduazione sulla barra di scorrimento verticale.

3. Aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati** all'area di lavoro nel riquadro dei risultati di riepilogo.

     ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Il `purchaseOrder` nodo e il nodo vengono visualizzati uno accanto `PurchaseOrderType` all'altro nell'area di progettazione [Graph Visualizzazione](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.
