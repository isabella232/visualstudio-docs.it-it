---
title: Aggiungere i nodi dei risultati di ricerca del set di XML Schema all'area di lavoro
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1bdb21c2b9ce3f6a79bf24738c84fcb3064c24cb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592789"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro

In questo argomento viene illustrato come aggiungere nodi evidenziati in **XML Schema Explorer** come risultato di una ricerca di parole chiave nell'area di lavoro.

> [!NOTE]
> È possibile aggiungere solo nodi globali all' [area di lavoro](../xml-tools/xml-schema-designer-workspace.md).

In questo esempio viene usato lo [schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md)di esempio.

## <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi

1. Seguire i passaggi in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Digitare "purchaseOrder" nella casella di testo Cerca della barra degli strumenti di [XML Explorer](../xml-tools/xml-schema-explorer.md) e fare clic sul pulsante Cerca.

     ![Ricerca di parole chiave in XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif)

     I risultati della ricerca sono evidenziati in **XML Schema Explorer** e contrassegnati con i segni di avanzamento sulla barra di scorrimento verticale.

3. Aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati all'area di lavoro** nel riquadro dei risultati di riepilogo.

     ![Risultato della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif)

     Il nodo `purchaseOrder` e il nodo `PurchaseOrderType` vengono visualizzati uno accanto all'altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.
