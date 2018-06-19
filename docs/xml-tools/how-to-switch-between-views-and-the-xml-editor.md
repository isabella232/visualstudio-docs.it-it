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
ms.openlocfilehash: 0b0eb90f2ead313ce94d609d71385b595f3e964b
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
ms.locfileid: "34477730"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procedura: passare dalle visualizzazioni l'Editor XML

In questo argomento viene illustrato come passare dalle visualizzazioni di Progettazione XML Schema (Progettazione XSD) all'editor XML. Questo esempio viene utilizzata la [schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Per passare dalle visualizzazioni all'editor XML

1.  Per creare e modificare un nuovo file di schema XML, seguire i passaggi descritti in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Per passare a Progettazione XML Schema dall'Editor XML, fare clic in un punto qualsiasi nell'Editor XML e selezionare **Progettazione viste**.

3.  Per passare alla visualizzazione grafico tramite la filigrana, scegliere il **utilizzare la visualizzazione grafico per visualizzare la relazione tra i nodi** collegamento nella visualizzazione iniziale.

4.  Trascinare il `USAddress` nodo il **XML Schema Explorer** alla visualizzazione grafico. Fare doppio clic su di `USAddress` nodo nella visualizzazione grafico e selezionare **Mostra nella visualizzazione modello di contenuto** nel menu di scelta rapida.

     Viene aperta la visualizzazione modello di contenuto con i dettagli del nodo `USAddress`.

5.  Per passare alla visualizzazione iniziale dalla visualizzazione modello di contenuto tramite la barra degli strumenti, scegliere il **visualizzazione iniziale** pulsante sulla barra degli strumenti XSD.

6.  Per passare tra le visualizzazioni usando i tasti di scelta, premere **Ctrl**+**1** per la visualizzazione iniziale **Ctrl**+**2** per la visualizzazione grafico e **Ctrl**+**3** per la visualizzazione modello di contenuto.

7.  Per passare all'Editor XML dalla visualizzazione modello di contenuto, il pulsante destro del nodo e selezionare **Visualizza codice** nel menu di scelta rapida.