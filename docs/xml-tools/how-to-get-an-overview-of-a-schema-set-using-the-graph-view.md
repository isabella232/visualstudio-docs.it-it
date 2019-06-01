---
title: 'Progettazione XML Schema: Ottenere informazioni generali sui set di schemi tramite visualizzazione grafico'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a0fc62a0d6dfe772a550f33cafa02bc5bc1bf3
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432168"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Procedura: Panoramica di uno schema impostato tramite la visualizzazione grafico

In questo argomento viene descritto come utilizzare il [visualizzazione grafico](../xml-tools/graph-view.md) per ottenere una visualizzazione di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file di XML Schema e salvare il file come *Relationships*.

2. Scegliere il **l'editor XML di uso per visualizzare e modificare il file di XML Schema sottostante** collegamento nella visualizzazione iniziale.

3. Copiare il codice di esempio di XML Schema da [dello schema XML di esempio: relazioni](../xml-tools/sample-xsd-file-relationships.md) e incollarlo per sostituire il codice che è stato aggiunto il nuovo file XSD per impostazione predefinita.

4. Fare doppio clic in un punto qualsiasi nell'editor XML e selezionare **Progettazione viste**.

5. Selezionare la visualizzazione grafico dal **sulla barra degli strumenti XSD**.

6. Selezionare **del Set di schemi** nodo il **XML Schema Explorer** e trascinare il nodo nell'area di progettazione della visualizzazione grafico. Dovrebbero essere visualizzati i nodi globali e le frecce che collegano i nodi tra cui intercorrono relazioni.

     ![Visualizzazione grafico](../xml-tools/media/relationshipingraphview.gif)

7. Fare clic su qualsiasi nodo nell'area di progettazione e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Rick, fare clic su qualsiasi nodo dell'elemento nell'area di progettazione e seleziona **genera XML di esempio** per visualizzare il documento di istanza XML.