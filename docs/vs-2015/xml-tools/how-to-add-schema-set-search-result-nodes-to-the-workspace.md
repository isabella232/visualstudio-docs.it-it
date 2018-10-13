---
title: "Procedura: aggiungere nodi dei risultati ricerca Set di schemi all'area di lavoro | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75f254a8f64c3750a3c89e10016a0520d3760847
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210366"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In questo argomento viene illustrato come aggiungere nodi evidenziati in XML Schema Explorer come risultato di una ricerca per parole chiave nell'area di lavoro.  
  
> [!NOTE]
>  Solo nodi globali possono essere aggiunti per il [dell'area di lavoro](../xml-tools/xml-schema-designer-workspace.md).  
  
 Questo esempio Usa il codice di esempio [Schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi  
  
1.  Seguire i passaggi descritti in [procedura: creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) sulla barra degli strumenti e fare clic sul pulsante di ricerca.  
  
     ![Ricerca per parole chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     I risultati della ricerca sono evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.  
  
3.  Aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.  
  
     ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Il `purchaseOrder` nodo e il `PurchaseOrderType` sono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.



