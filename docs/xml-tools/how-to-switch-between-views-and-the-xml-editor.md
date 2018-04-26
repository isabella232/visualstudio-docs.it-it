---
title: "Procedura: passare dalle visualizzazioni all'editor XML"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9109b94f66a440b91e136266df6a8f896a01edcd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procedura: passare dalle visualizzazioni all'editor XML

In questo argomento viene illustrato come passare dalle visualizzazioni di Progettazione XML Schema (Progettazione XSD) all'editor XML. Questo esempio viene utilizzato il [Schema ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Per passare dalle visualizzazioni all'editor XML

1.  Per creare e modificare un nuovo file di XML Schema, seguire i passaggi in [procedura: creare e modificare un File di Schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Per passare a Progettazione XML Schema dall'Editor XML, fare clic in un punto qualsiasi nell'Editor XML e selezionare **Visualizza finestra di progettazione**.

3.  Per passare alla visualizzazione grafico tramite la filigrana, scegliere il **utilizzare la visualizzazione grafico per visualizzare la relazione tra i nodi** collegamento nella visualizzazione iniziale.

4.  Trascinare il nodo `USAddress` da XML Schema Explorer alla visualizzazione grafico. Fare doppio clic su di `USAddress` nodo nella visualizzazione grafico e selezionare **Mostra nella visualizzazione modello di contenuto** nel menu di scelta rapida.

     Viene aperta la visualizzazione modello di contenuto con i dettagli del nodo `USAddress`.

5.  Per passare alla visualizzazione iniziale dalla visualizzazione modello di contenuto tramite la barra degli strumenti, fare clic sul pulsante Visualizzazione iniziale sulla barra degli strumenti XSD.

6.  Per passare da una visualizzazione all'altra tramite i tasti di scelta, premere CTRL+1 per la visualizzazione iniziale, CTRL+2 per la visualizzazione grafico e CTRL+3 per la visualizzazione modello di contenuto.

7.  Per passare all'Editor XML dalla visualizzazione modello di contenuto, il pulsante destro del nodo e selezionare **Visualizza codice** nel menu di scelta rapida.