---
title: Esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto in Progettazione XML Schema
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63edeb597c3c085df3c9c9eb15f6c051e524a476
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525999"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procedura: Esaminare il modello di contenuto dei nodi tramite la visualizzazione modello di contenuto

In questo argomento viene descritto come esaminare i nodi usando il [visualizzazione modello di contenuto](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1.  Creare un nuovo file XML Schema.

2.  Fare clic su **l'editor XML di uso per visualizzare e modificare il file di XML Schema sottostante** nella visualizzazione iniziale.

3.  Copiare il codice di esempio di XML Schema da [dello schema XML di esempio: schema di ordine di acquisto](../xml-tools/sample-xsd-file-purchase-order-schema.md) e incollarlo per sostituire il codice che è stato aggiunto il nuovo file XSD per impostazione predefinita.

4.  Selezionare il `purchaseOrder` elemento in Schema Explorer facendo clic con il `purchaseOrder` elemento nello schema XML editor e selezionando **Mostra in XML Explorer**.

5.  Fare doppio clic il `purchaseOrder` in XML Explorer e selezionare **Mostra nella visualizzazione modello di contenuto**.

     Nella visualizzazione modello di contenuto viene visualizzato l'elemento `purchaseOrder` sulla relativa area di progettazione.

6.  Espandere i nodi `shipTo`, `billTo` e `items` facendo doppio clic su ogni nodo o facendo clic sulla doppia freccia a destra di ogni nodo.

     I nodi dell'elemento `purchaseOrder` ora sono espansi ed è possibile visualizzare il modello di contenuto dell'elemento.

7.  Fare clic su qualsiasi nodo nell'elemento `purchaseOrder` e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8.  Scegliere il **Mostra documentazione** pulsante sulla barra degli strumenti XSD per attivare/disattivare documentazione. È anche possibile fare clic con il pulsante destro del mouse sull'area di progettazione per attivare o disattivare la documentazione.

9. Rick-scegliere il `purchaseOrder` nodo e selezionare **genera XML di esempio** per visualizzare il documento di istanza XML.