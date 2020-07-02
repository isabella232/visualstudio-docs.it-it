---
title: Esaminare i nodi tramite la visualizzazione modello di contenuto in Progettazione XML Schema
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bf6294aeac9a23168bf9cf9aaec26efbfc6c1f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815981"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procedura: esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto

In questo argomento viene descritto come esplorare i nodi utilizzando la [visualizzazione modello di contenuto](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file XML Schema.

2. Fare clic su **Usa editor XML per visualizzare e modificare il file di XML schema sottostante** nella visualizzazione iniziale.

3. Copiare il codice di esempio XML Schema da [esempio XML Schema: schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md) e incollarlo per sostituire il codice aggiunto al nuovo file XSD per impostazione predefinita.

4. Per selezionare l'elemento in Esplora schema, fare clic con il `purchaseOrder` pulsante destro del mouse sull' `purchaseOrder` elemento nell'editor XML e scegliere **Mostra in Esplora XML**.

5. Fare clic con il pulsante destro del mouse su `purchaseOrder` in XML Explorer e selezionare **Mostra nella visualizzazione modello di contenuto**.

     Nella visualizzazione modello di contenuto viene visualizzato l'elemento `purchaseOrder` sulla relativa area di progettazione.

6. Espandere i nodi `shipTo`, `billTo` e `items` facendo doppio clic su ogni nodo o facendo clic sulla doppia freccia a destra di ogni nodo.

     I nodi dell'elemento `purchaseOrder` ora sono espansi ed è possibile visualizzare il modello di contenuto dell'elemento.

7. Fare clic su qualsiasi nodo nell'elemento `purchaseOrder` e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Fare clic sul pulsante **Mostra documentazione** sulla barra degli strumenti XSD per impostare la documentazione. È anche possibile fare clic con il pulsante destro del mouse sull'area di progettazione per attivare o disattivare la documentazione.

9. Fare clic con il pulsante destro del mouse sul `purchaseOrder` nodo e selezionare **genera XML di esempio** per visualizzare il documento dell'istanza XML.
