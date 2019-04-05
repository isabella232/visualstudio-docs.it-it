---
title: 'Procedura: Panoramica di un Set di schemi tramite la visualizzazione grafico | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 61284d0b94d621c788a4d39fc2672d0778dd5c0f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965261"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Procedura: Ottenere una panoramica di un set di schemi tramite la visualizzazione grafico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In questo argomento viene descritto come utilizzare il [visualizzazione grafico](../xml-tools/graph-view.md) per ottenere una visualizzazione di alto livello dei nodi in un set di schemi e le relazioni tra i nodi.  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Per creare un nuovo file XSD e visualizzare l'elemento radice nella visualizzazione modello di contenuto  
  
1.  Creare un nuovo file XML Schema e salvare il file come Relationships.xsd.  
  
2.  Scegliere il **usare l'Editor XML per visualizzare e modificare il file di XML Schema sottostante** collegamento nella visualizzazione iniziale.  
  
3.  Copiare il codice di esempio di XML Schema da [XML Schema di esempio: Le relazioni](../xml-tools/sample-xsd-file-relationships.md) e incollarlo per sostituire il codice che è stato aggiunto il nuovo file XSD per impostazione predefinita.  
  
4.  Fare doppio clic in un punto qualsiasi dell'Editor XML e selezionare **Progettazione viste**.  
  
5.  Selezionare la visualizzazione grafico dalla barra degli strumenti XSD.  
  
6.  Selezionare **del Set di schemi** nodo nel XML Schema Explorer e trascinare il nodo alla visualizzazione del grafico nell'area di progettazione. Dovrebbero essere visualizzati i nodi globali e le frecce che collegano i nodi tra cui intercorrono relazioni.  
  
     ![Visualizzazione grafico](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")  
  
7.  Fare clic su qualsiasi nodo nell'area di progettazione e analizzare la barra di navigazione per vedere dove si trova il nodo selezionato nel set di schemi.  
  
8.  Rick, fare clic su qualsiasi nodo dell'elemento nell'area di progettazione e seleziona **genera XML di esempio** per visualizzare il documento di istanza XML.
