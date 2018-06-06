---
title: Aggiungere nodi dei risultati ricerca Set XML Schema per l'area di lavoro
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04e74057bd059c82010678b7de571ff180e7fbfe
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751910"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: aggiungere nodi dei risultati ricerca set schema all'area di lavoro

In questo argomento viene illustrato come aggiungere nodi evidenziati nel **XML Schema Explorer** come risultato di una ricerca per parole chiave nell'area di lavoro.

> [!NOTE]
> Possono essere aggiunti solo nodi globali per il [dell'area di lavoro](../xml-tools/xml-schema-designer-workspace.md).


 Questo esempio viene utilizzato l'esempio [schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi

1.  Seguire i passaggi descritti in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Digitare "purchaseOrder" nella casella di testo di ricerca del [XML Explorer](../xml-tools/xml-schema-explorer.md) barra degli strumenti e fare clic sul pulsante di ricerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     I risultati della ricerca vengono evidenziati nel **XML Schema Explorer** e contrassegnato dal segno di spunta sulla barra di scorrimento verticale.

3.  Aggiungere i risultati della ricerca all'area di lavoro, fare clic il **Aggiungi nodi evidenziati all'area di lavoro** pulsante del riquadro dei risultati di riepilogo.

     ![Risultati della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Il `purchaseOrder` nodo e `PurchaseOrderType` nodo vengono visualizzati uno accanto a altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.