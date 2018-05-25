---
title: "Procedura: aggiungere nodi all'area di lavoro da XML Schema Explorer"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 487cb4fe5ea15c2186f9284c557a1e9377ac801f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedura: aggiungere nodi all'area di lavoro da XML Schema Explorer

In questo argomento viene illustrato come aggiungere nodi per il [dell'area di lavoro di progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md) dal **XML Schema Explorer**. A questo scopo trascinando e rilasciando i nodi dal **XML Schema Explorer** su una visualizzazione di progettazione XSD o tramite il **XML Schema Explorer** menu di scelta rapida. È inoltre possibile aggiungere nodi evidenziati come risultato di una ricerca eseguita con il **XML Schema Explorer**. Per altre informazioni, vedere [procedura: aggiungere nodi dei risultati ricerca set schema all'area di lavoro](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Possono aggiungere solo nodi globali per il [dell'area di lavoro di progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Per aggiungere nodi tramite il menu di scelta rapida Esplora XML

1.  Seguire i passaggi descritti in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Fare clic con il pulsante destro sul `PurchaseOrderType` nodo in XSD Explorer. Selezionare **Mostra in visualizzazione grafico**.

     Il nodo `purchaseOrderType` viene visualizzato nell'area di progettazione della visualizzazione grafico.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Per trascinare e rilasciare un nodo su una visualizzazione

1.  Fare clic sul `PurchaseOrderType` nodo nella visualizzazione grafico. Selezionare **Mostra in XML Schema Explorer**.

     Il nodo viene evidenziato nel **XML Schema Explorer**.

2.  Fare clic con il pulsante destro sul `PurchaseOrderType` nodo il **XML Schema Explorer** e selezionare **Mostra tutti i riferimenti**.

     Il nodo `purchaseOrder` viene evidenziato.

3.  Trascinare il nodo `purchaseOrder` sulla visualizzazione grafico.

     I nodi `purchaseOrder` e `PurchaseOrderType` sono visualizzati uno accanto all'altro nell'area di progettazione della visualizzazione grafico. Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Per aggiungere nodi tramite la funzionalità di ricerca di Schema Explorer

1.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) barra degli strumenti e fare clic sul pulsante di ricerca.

     ![Ricerca di parola chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     I risultati della ricerca vengono evidenziati nel **XML Schema Explorer** e contrassegnato dal segno di spunta sulla barra di scorrimento verticale.

2.  Aggiungere i risultati della ricerca all'area di lavoro, fare clic il **Aggiungi nodi evidenziati all'area di lavoro** pulsante del riquadro dei risultati di riepilogo.

     ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Il `purchaseOrder` nodo e `PurchaseOrderType` nodo vengono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)