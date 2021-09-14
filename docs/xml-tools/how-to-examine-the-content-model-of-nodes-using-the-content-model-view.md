---
title: Esaminare il modello di contenuto dei nodi
description: Informazioni su come usare la visualizzazione modello di contenuto in Progettazione XML Schema per esaminare il modello di contenuto dei nodi in un XML Schema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: a9e1b5d1ebd573f74762d86717118138adea23d7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633620"
---
# <a name="how-to-examine-the-content-model-of-nodes-by-using-the-content-model-view"></a>Procedura: Esaminare il modello di contenuto dei nodi usando la visualizzazione modello di contenuto

Questo argomento descrive come esplorare i nodi usando la visualizzazione modello [di contenuto](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file XML Schema.

2. Fare **clic su Usa editor XML per visualizzare e modificare il file XML Schema** sottostante nella visualizzazione iniziale.

3. Copiare il codice di esempio di XML Schema da Schema XML di [esempio: schema](../xml-tools/sample-xsd-file-purchase-order-schema.md) dell'ordine di acquisto e incollarlo per sostituire il codice aggiunto al nuovo file XSD per impostazione predefinita.

4. Selezionare l'elemento in Esplora schemi facendo clic con il pulsante destro del mouse sull'elemento nell'editor XML e `purchaseOrder` scegliendo Mostra in XML `purchaseOrder` **Explorer.**

5. Fare clic con il pulsante `purchaseOrder` destro del mouse su in XML Explorer e scegliere Mostra nella visualizzazione modello di **contenuto**.

     Nella visualizzazione modello di contenuto viene visualizzato l'elemento `purchaseOrder` sulla relativa area di progettazione.

6. Espandere i nodi `shipTo`, `billTo` e `items` facendo doppio clic su ogni nodo o facendo clic sulla doppia freccia a destra di ogni nodo.

     I nodi dell'elemento `purchaseOrder` ora sono espansi ed è possibile visualizzare il modello di contenuto dell'elemento.

7. Fare clic su qualsiasi nodo nell'elemento `purchaseOrder` e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Fare clic sul **pulsante Mostra** documentazione nella barra degli strumenti XSD per attivare o disattivare la documentazione. È anche possibile fare clic con il pulsante destro del mouse sull'area di progettazione per attivare o disattivare la documentazione.

9. Fare clic con il pulsante destro `purchaseOrder` del mouse sul nodo e scegliere Genera XML **di** esempio per visualizzare il documento dell'istanza XML.
