---
title: "Procedura: aggiungere nodi all'area di lavoro da XML Schema Explorer | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c8fe9d5ba8c096a03de7a9df85945f4aeb4a0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656338"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedura: aggiungere nodi all'area di lavoro da XML Schema Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come aggiungere nodi all' [area di lavoro di progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md) da XML Schema Explorer. È possibile trascinare e rilasciare nodi da XML Schema Explorer su una visualizzazione di Progettazione XSD o tramite il menu di scelta rapida di XML Schema Explorer. È anche possibile aggiungere nodi evidenziati come risultato di una ricerca eseguita da XML Schema Explorer. Per ulteriori informazioni, vedere [procedura: aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> È possibile aggiungere solo nodi globali all' [area di lavoro di progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md).

### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Per aggiungere nodi tramite il menu di scelta rapida di XML Explorer

1. Seguire i passaggi in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Fare clic con il pulsante destro del mouse sul nodo `PurchaseOrderType` in XSD Explorer. Selezionare **Mostra in visualizzazione grafico**.

     Il nodo `purchaseOrderType` viene visualizzato nell'area di progettazione della visualizzazione grafico.

### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Per trascinare e rilasciare un nodo su una visualizzazione

1. Fare clic con il pulsante destro del mouse sul nodo `PurchaseOrderType` nella visualizzazione grafico. Selezionare **Mostra in XML Schema Explorer**.

     Il nodo viene evidenziato in XML Schema Explorer.

2. Fare clic con il pulsante destro del mouse sul `PurchaseOrderType` nodo in XML Schema Explorer e scegliere **Mostra tutti i riferimenti**.

     Il nodo `purchaseOrder` viene evidenziato.

3. Trascinare il nodo `purchaseOrder` sulla visualizzazione grafico.

     I nodi `purchaseOrder` e `PurchaseOrderType` sono visualizzati uno accanto all'altro nell'area di progettazione della visualizzazione grafico. Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Per aggiungere nodi tramite la funzionalità di ricerca di Schema Explorer

1. Digitare "purchaseOrder" nella casella di testo Cerca della barra degli strumenti di [XML Explorer](../xml-tools/xml-schema-explorer.md) e fare clic sul pulsante Cerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     I risultati della ricerca sono evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.

2. Aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati all'area di lavoro** nel riquadro dei risultati di riepilogo.

     ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Il `purchaseOrder` nodo e il `PurchaseOrderType` nodo vengono visualizzati uno accanto all'altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="see-also"></a>Vedere anche
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
