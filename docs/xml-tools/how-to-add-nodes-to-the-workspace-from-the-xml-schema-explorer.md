---
title: Aggiungere nodi all'area di lavoro da XML Schema Explorer
description: Informazioni su come aggiungere nodi all'area di lavoro Progettazione XML Schema da XML Schema Explorer usando il menu di scelta rapida o trascinando e rilasciando nodi in una visualizzazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 4c55f920d07d2f6230022d78a2a98b77cb86ebd2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045593"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedura: Aggiungere nodi all'area di lavoro da ESPLORA XML Schema

In questo argomento viene illustrato come aggiungere nodi all'area di lavoro [Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md) da Xml Schema **Explorer.** A tale scopo, trascinare e rilasciare nodi da **ESPLORA XML Schema** in una visualizzazione Progettazione XSD o tramite il menu di scelta rapida di Esplora XML **Schema.** È anche possibile aggiungere nodi evidenziati come risultato di una ricerca eseguita da **XML Schema Explorer.** Per altre informazioni, vedere Procedura: Aggiungere nodi dei risultati della [ricerca del set di schemi all'area di lavoro](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> All'area di lavoro Progettazione XML Schema è possibile aggiungere [solo nodi globali.](../xml-tools/xml-schema-designer-workspace.md)

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Per aggiungere nodi tramite il menu di scelta rapida di Esplora XML

1. Seguire la procedura descritta in [Procedura: Creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Fare clic con il pulsante `PurchaseOrderType` destro del mouse sul nodo in Xsd Explorer. Selezionare **Mostra nella Graph visualizzazione**.

     Il nodo `purchaseOrderType` viene visualizzato nell'area di progettazione della visualizzazione grafico.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Per trascinare e rilasciare un nodo su una visualizzazione

1. Fare clic con il pulsante destro `PurchaseOrderType` del mouse sul nodo Graph visualizzazione. Selezionare **Mostra in XML Schema Explorer**.

     Il nodo è evidenziato in **XML Schema Explorer.**

2. Fare clic con il pulsante `PurchaseOrderType` destro del mouse sul nodo in XML Schema **Explorer** e selezionare Mostra tutti **i riferimenti**.

     Il nodo `purchaseOrder` viene evidenziato.

3. Trascinare il nodo `purchaseOrder` sulla visualizzazione grafico.

     I nodi `purchaseOrder` e `PurchaseOrderType` sono visualizzati uno accanto all'altro nell'area di progettazione della visualizzazione grafico. Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Per aggiungere nodi tramite la funzionalità di ricerca di Schema Explorer

1. Digitare "purchaseOrder" nella casella di testo di ricerca della barra degli strumenti [di XML Explorer](../xml-tools/xml-schema-explorer.md) e fare clic sul pulsante di ricerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     I risultati della ricerca sono evidenziati in **XML Schema Explorer** e contrassegnati da segni di graduazione sulla barra di scorrimento verticale.

2. Aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati** all'area di lavoro nel riquadro dei risultati di riepilogo.

     ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Il `purchaseOrder` nodo e il nodo vengono visualizzati uno accanto `PurchaseOrderType` all'altro nell'area di progettazione [del](../xml-tools/graph-view.md)Graph Visualizza . Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.

## <a name="see-also"></a>Vedi anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
