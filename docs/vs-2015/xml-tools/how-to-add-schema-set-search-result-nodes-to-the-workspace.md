---
title: "Procedura: Aggiungere nodi dei risultati ricerca Set di schemi all'area di lavoro | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 086a21e7793e3823615181037b24bcfb7cc5d461
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967029"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: Aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In questo argomento viene illustrato come aggiungere nodi evidenziati in XML Schema Explorer come risultato di una ricerca per parole chiave nell'area di lavoro.  
  
> [!NOTE]
>  Solo nodi globali possono essere aggiunti per il [dell'area di lavoro](../xml-tools/xml-schema-designer-workspace.md).  
  
 Questo esempio Usa il codice di esempio [Schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md).  
  
### <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi  
  
1.  Seguire i passaggi in [come: Creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) sulla barra degli strumenti e fare clic sul pulsante di ricerca.  
  
     ![Ricerca per parole chiave XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     I risultati della ricerca sono evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.  
  
3.  Aggiungere i risultati della ricerca all'area di lavoro facendo il **Aggiungi nodi evidenziati all'area di lavoro** pulsante nel riquadro dei risultati di riepilogo.  
  
     ![Risultato di ricerca XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     Il `purchaseOrder` nodo e il `PurchaseOrderType` sono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.
