---
title: "Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 578a50d8fae4047b6e36338f8067561c9e4e9636
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935901"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer

Questo argomento illustra come aggiungere nodi al [dell'area di lavoro Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md) dalle **XML Schema Explorer**. Questo scopo, trascinare e rilasciare nodi dal **XML Schema Explorer** su una visualizzazione di progettazione XSD o tramite il **XML Schema Explorer** menu di scelta rapida. È anche possibile aggiungere nodi evidenziati come risultato di una ricerca eseguita con il **XML Schema Explorer**. Per altre informazioni, vedere [Procedura: Aggiungere nodi dei risultati ricerca set di schemi all'area di lavoro](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Solo nodi globali possono essere aggiunti per il [dell'area di lavoro Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Per aggiungere nodi tramite il menu di scelta rapida di XML Explorer

1.  Seguire i passaggi in [come: Creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Fare clic con il pulsante destro sul `PurchaseOrderType` nodo in XSD Explorer. Selezionare **Mostra in visualizzazione grafico**.

     Il nodo `purchaseOrderType` viene visualizzato nell'area di progettazione della visualizzazione grafico.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Per trascinare e rilasciare un nodo su una visualizzazione

1.  Fare clic su di `PurchaseOrderType` nodo nella visualizzazione grafico. Selezionare **Mostra in XML Schema Explorer**.

     Il nodo viene evidenziato nel **XML Schema Explorer**.

2.  Fare clic con il pulsante destro sul `PurchaseOrderType` nodo il **XML Schema Explorer** e selezionare **Mostra tutti i riferimenti**.

     Il nodo `purchaseOrder` viene evidenziato.

3.  Trascinare il nodo `purchaseOrder` sulla visualizzazione grafico.

     I nodi `purchaseOrder` e `PurchaseOrderType` sono visualizzati uno accanto all'altro nell'area di progettazione della visualizzazione grafico. Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Per aggiungere nodi tramite la funzionalità di ricerca di Schema Explorer

1.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) sulla barra degli strumenti e fare clic sul pulsante di ricerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     I risultati della ricerca sono evidenziati nel **XML Schema Explorer** e contrassegnato dal segno di spunta sulla barra di scorrimento verticale.

2.  Aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.

     ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Il `purchaseOrder` nodo e il `PurchaseOrderType` sono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)