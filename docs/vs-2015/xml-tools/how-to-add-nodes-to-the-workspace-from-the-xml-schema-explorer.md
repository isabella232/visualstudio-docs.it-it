---
title: "Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1fef367b36a683111369b656c8c1ba5a285fe6df
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417472"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come aggiungere nodi per il [dell'area di lavoro Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md) da XML Schema Explorer. È possibile trascinare e rilasciare nodi da XML Schema Explorer su una visualizzazione di Progettazione XSD o tramite il menu di scelta rapida di XML Schema Explorer. È anche possibile aggiungere nodi evidenziati come risultato di una ricerca eseguita da XML Schema Explorer. Per altre informazioni, vedere [Procedura: Aggiungere nodi dei risultati ricerca Set di schemi all'area di lavoro](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
> Solo nodi globali possono essere aggiunti per il [area di lavoro Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Per aggiungere nodi tramite il menu di scelta rapida di XML Explorer  
  
1. Seguire i passaggi in [come: Creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2. Fare clic con il pulsante destro del mouse sul nodo `PurchaseOrderType` in XSD Explorer. Selezionare **Mostra in visualizzazione grafico**.  
  
     Il nodo `purchaseOrderType` viene visualizzato nell'area di progettazione della visualizzazione grafico.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Per trascinare e rilasciare un nodo su una visualizzazione  
  
1. Fare clic con il pulsante destro del mouse sul nodo `PurchaseOrderType` nella visualizzazione grafico. Selezionare **Mostra in XML Schema Explorer**.  
  
     Il nodo viene evidenziato in XML Schema Explorer.  
  
2. Fare clic con il pulsante destro sul `PurchaseOrderType` nodo di XML Schema Explorer e selezionare **Mostra tutti i riferimenti**.  
  
     Il nodo `purchaseOrder` viene evidenziato.  
  
3. Trascinare il nodo `purchaseOrder` sulla visualizzazione grafico.  
  
     I nodi `purchaseOrder` e `PurchaseOrderType` sono visualizzati uno accanto all'altro nell'area di progettazione della visualizzazione grafico. Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Per aggiungere nodi tramite la funzionalità di ricerca di Schema Explorer  
  
1. Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) sulla barra degli strumenti e fare clic sul pulsante di ricerca.  
  
     ![Ricerca per parole chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     I risultati della ricerca sono evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.  
  
2. Aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.  
  
     ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Il `purchaseOrder` nodo e il `PurchaseOrderType` sono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.  
  
## <a name="see-also"></a>Vedere anche  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
