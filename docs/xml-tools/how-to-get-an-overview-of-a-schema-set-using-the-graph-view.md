---
title: Ottenere una panoramica di un set di schemi
description: 'Progettazione XML Schema: informazioni su come utilizzare la visualizzazione grafico in XML Schema Explorer per visualizzare una vista di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 896522f6d7f057d359cb5502c42edf34d0a2d823
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897459"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Procedura: ottenere una panoramica di un set di schemi tramite la visualizzazione grafico

In questo argomento viene descritto come utilizzare la [visualizzazione grafico](../xml-tools/graph-view.md) per visualizzare una vista di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file XML Schema e salvare il file come *relationships. xsd*.

2. Fare clic su **Usa editor XML per visualizzare e modificare il collegamento al file di XML schema sottostante** nella visualizzazione iniziale.

3. Copiare il codice di esempio XML Schema da [XML Schema di esempio: relazioni](../xml-tools/sample-xsd-file-relationships.md) e incollarlo per sostituire il codice aggiunto al nuovo file XSD per impostazione predefinita.

4. Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML e selezionare **Progettazione visualizzazioni**.

5. Selezionare la visualizzazione grafico dalla **barra degli strumenti XSD**.

6. Selezionare nodo **set di schemi** in **XML Schema Explorer** e trascinare il nodo nell'area di progettazione della visualizzazione grafico. Dovrebbero essere visualizzati i nodi globali e le frecce che collegano i nodi tra cui intercorrono relazioni.

     ![Visualizzazione grafico](../xml-tools/media/relationshipingraphview.gif)

7. Fare clic su qualsiasi nodo nell'area di progettazione e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Fare clic con il pulsante destro del mouse su qualsiasi nodo elemento nell'area di progettazione e selezionare **genera XML di esempio** per visualizzare il documento dell'istanza XML.
