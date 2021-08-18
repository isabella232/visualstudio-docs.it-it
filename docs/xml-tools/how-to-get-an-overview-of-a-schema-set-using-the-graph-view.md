---
title: Ottenere una panoramica di un set di schemi
description: 'Progettazione XML Schema: informazioni su come usare la vista Graph in XML Schema Explorer per visualizzare una visualizzazione di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1461653dff8e757ec462a3d47eb76ba7ed4f0ed5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135078"
---
# <a name="how-to-get-an-overview-of-a-schema-set-by-using-the-graph-view"></a>Procedura: Ottenere una panoramica di un set di schemi usando la Graph dati

Questo argomento descrive come usare la visualizzazione [Graph](../xml-tools/graph-view.md) per visualizzare una visualizzazione di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file XML Schema e salvare il file *come Relationships.xsd.*

2. Fare clic **sul collegamento Usa editor XML per visualizzare e modificare** il file XML Schema sottostante nella visualizzazione iniziale.

3. Copiare il codice di esempio di XML Schema dalle relazioni [Di esempio di XML Schema:](../xml-tools/sample-xsd-file-relationships.md) e incollarlo per sostituire il codice aggiunto al nuovo file XSD per impostazione predefinita.

4. Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML **e Progettazione visualizzazioni**.

5. Selezionare la visualizzazione Graph sulla barra **degli strumenti XSD**.

6. Selezionare **il nodo Set** di schemi in XML Schema Explorer **e** trascinarlo nell'area di progettazione della Graph schema. Dovrebbero essere visualizzati i nodi globali e le frecce che collegano i nodi tra cui intercorrono relazioni.

     ![Visualizzazione grafico](../xml-tools/media/relationshipingraphview.gif)

7. Fare clic su qualsiasi nodo nell'area di progettazione e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Fare clic su qualsiasi nodo elemento nell'area di progettazione e selezionare **Generate Sample XML** (Genera XML di esempio) per visualizzare il documento dell'istanza XML.
