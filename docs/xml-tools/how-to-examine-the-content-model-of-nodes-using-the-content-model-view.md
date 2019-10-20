---
title: Esaminare i nodi tramite la visualizzazione modello di contenuto in Progettazione XML Schema
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c109d167534dc969ae34c55d16f2ee55e34fe3aa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645891"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procedura: esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto

In questo argomento viene descritto come esplorare i nodi utilizzando la [visualizzazione modello di contenuto](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file XML Schema.

2. Fare clic su **Usa editor XML per visualizzare e modificare il file di XML schema sottostante** nella visualizzazione iniziale.

3. Copiare il codice di esempio XML Schema da [esempio XML Schema: schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md) e incollarlo per sostituire il codice aggiunto al nuovo file XSD per impostazione predefinita.

4. Per selezionare l'elemento `purchaseOrder` in Esplora schema, fare clic con il pulsante destro del mouse sull'elemento `purchaseOrder` nell'editor XML e scegliere **Mostra in Esplora XML**.

5. Fare clic con il pulsante destro del mouse sul `purchaseOrder` in XML Explorer e scegliere **Mostra in visualizzazione modello di contenuto**.

     Nella visualizzazione modello di contenuto viene visualizzato l'elemento `purchaseOrder` sulla relativa area di progettazione.

6. Espandere i nodi `shipTo`, `billTo` e `items` facendo doppio clic su ogni nodo o facendo clic sulla doppia freccia a destra di ogni nodo.

     I nodi dell'elemento `purchaseOrder` ora sono espansi ed è possibile visualizzare il modello di contenuto dell'elemento.

7. Fare clic su qualsiasi nodo nell'elemento `purchaseOrder` e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Fare clic sul pulsante **Mostra documentazione** sulla barra degli strumenti XSD per impostare la documentazione. È anche possibile fare clic con il pulsante destro del mouse sull'area di progettazione per attivare o disattivare la documentazione.

9. Fare clic con il pulsante destro del mouse sul nodo `purchaseOrder` e selezionare **genera XML di esempio** per visualizzare il documento dell'istanza XML.
