---
title: Aggiungere nodi dei risultati ricerca Set XML Schema per l'area di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7cb8e66292a1cdb393401d180bd8b9f8691dc8f0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913928"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: Aggiungere nodi dei risultati ricerca set di schemi all'area di lavoro

In questo argomento viene illustrato come aggiungere nodi evidenziati nel **XML Schema Explorer** come risultato di una ricerca per parole chiave nell'area di lavoro.

> [!NOTE]
> Solo nodi globali possono essere aggiunti per il [dell'area di lavoro](../xml-tools/xml-schema-designer-workspace.md).


 Questo esempio Usa il codice di esempio [schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi

1.  Seguire i passaggi in [come: Creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) sulla barra degli strumenti e fare clic sul pulsante di ricerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     I risultati della ricerca sono evidenziati nel **XML Schema Explorer** e contrassegnato dal segno di spunta sulla barra di scorrimento verticale.

3.  Aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.

     ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Il `purchaseOrder` nodo e il `PurchaseOrderType` sono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.