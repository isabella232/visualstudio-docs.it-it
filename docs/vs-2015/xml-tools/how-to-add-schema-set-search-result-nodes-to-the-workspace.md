---
title: "Procedura: aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b34be331ad3ec67e2c3bd8d9ecc500cd256b1b09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666543"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Procedura: aggiungere nodi dei risultati di ricerca del set di schemi all'area di lavoro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come aggiungere nodi evidenziati in XML Schema Explorer come risultato di una ricerca per parole chiave nell'area di lavoro.

> [!NOTE]
> È possibile aggiungere solo nodi globali all' [area di lavoro](../xml-tools/xml-schema-designer-workspace.md).

 In questo esempio viene usato lo [schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md)di esempio.

### <a name="to-add-schema-set-result-nodes"></a>Per aggiungere nodi dei risultati del set di schemi

1. Seguire i passaggi in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Digitare "purchaseOrder" nella casella di testo Cerca della barra degli strumenti di [XML Explorer](../xml-tools/xml-schema-explorer.md) e fare clic sul pulsante Cerca.

     ![Ricerca parole chiave di XML Schema Explorer](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

     I risultati della ricerca sono evidenziati in XML Schema Explorer e contrassegnati con un segno di spunta sulla barra di scorrimento verticale.

3. Aggiungere i risultati della ricerca all'area di lavoro facendo clic sul pulsante **Aggiungi nodi evidenziati all'area di lavoro** nel riquadro dei risultati di riepilogo.

     ![Risultato della ricerca in XML Schema Explorer](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

     Il nodo `purchaseOrder` e il nodo `PurchaseOrderType` vengono visualizzati uno accanto all'altro nell'area di progettazione della [visualizzazione grafico](../xml-tools/graph-view.md). Poiché i due nodi sono correlati (l'elemento `purchaseOrder` è di tipo `PurchaseOrderType`), viene tracciata una freccia tra loro.
