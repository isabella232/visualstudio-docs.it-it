---
title: 'Procedura: ottenere una panoramica di un set di schemi tramite la visualizzazione grafico | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670888"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Procedura: ottenere una panoramica di un set di schemi tramite la visualizzazione grafico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene descritto come utilizzare la [visualizzazione grafico](../xml-tools/graph-view.md) per visualizzare una vista di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto

1. Creare un nuovo file XML Schema e salvare il file come Relationships.xsd.

2. Fare clic su **Usa editor XML per visualizzare e modificare il collegamento al file di XML schema sottostante** nella visualizzazione iniziale.

3. Copiare il codice di esempio XML Schema da [XML Schema di esempio: relazioni](../xml-tools/sample-xsd-file-relationships.md) e incollarlo per sostituire il codice aggiunto al nuovo file XSD per impostazione predefinita.

4. Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML e selezionare **Progettazione visualizzazioni**.

5. Selezionare la visualizzazione grafico dalla barra degli strumenti XSD.

6. Selezionare nodo **set di schemi** in XML Schema Explorer e trascinare il nodo in progettazione suface della visualizzazione grafico. Dovrebbero essere visualizzati i nodi globali e le frecce che collegano i nodi tra cui intercorrono relazioni.

     ![Visualizzazione grafico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. Fare clic su qualsiasi nodo nell'area di progettazione e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.

8. Fare clic con il pulsante destro del mouse su qualsiasi nodo elemento nella superficie di disegno e selezionare **genera XML di esempio** per visualizzare il documento dell'istanza XML.
