---
title: "Procedura: spostarsi tra le visualizzazioni e l'editor XML | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28267f705dd9a747d0e3f3ac5dc2869ab7de8f6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656313"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procedura: passare dalle visualizzazioni all'editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come passare dalle visualizzazioni di Progettazione XML Schema (Progettazione XSD) all'editor XML. In questo esempio viene usato lo [schema di ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md).

### <a name="to-switch-between-the-views-and-the-xml-editor"></a>Per passare dalle visualizzazioni all'editor XML

1. Per creare e modificare un nuovo file XML Schema, attenersi alla procedura illustrata in [procedura: creare e modificare un file di schema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Per passare a Progettazione XML schema dall'editor XML, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML e scegliere **Visualizza finestra di progettazione**.

3. Per passare alla visualizzazione grafico con la filigrana, fare clic su **Usa la visualizzazione grafico per visualizzare la relazione tra il collegamento nodi** nella visualizzazione iniziale.

4. Trascinare il nodo `USAddress` da XML Schema Explorer alla visualizzazione grafico. Fare clic con il pulsante destro del mouse sul `USAddress` nodo nella visualizzazione grafico e scegliere **Mostra in visualizzazione modello di contenuto** nel menu di scelta rapida.

     Viene aperta la visualizzazione modello di contenuto con i dettagli del nodo `USAddress`.

5. Per passare alla visualizzazione iniziale dalla visualizzazione modello di contenuto tramite la barra degli strumenti, fare clic sul pulsante Visualizzazione iniziale sulla barra degli strumenti XSD.

6. Per passare da una visualizzazione all'altra tramite i tasti di scelta, premere CTRL+1 per la visualizzazione iniziale, CTRL+2 per la visualizzazione grafico e CTRL+3 per la visualizzazione modello di contenuto.

7. Per passare all'editor XML dalla visualizzazione modello di contenuto, fare clic con il pulsante destro del mouse sul nodo e scegliere **Visualizza codice** nel menu di scelta rapida.
