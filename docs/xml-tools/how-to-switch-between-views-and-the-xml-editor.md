---
title: "Procedura: Passare da una visualizzazione all'altra e dall'editor XML"
description: Informazioni su come passare tra le visualizzazioni di Progettazione XML Schema (Progettazione XSD) e l'editor XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 1a6f9be548b725aa664cd6223ee2eb9891c77fdc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037746"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>Procedura: Passare da una visualizzazione all'altra e dall'editor XML

Questo argomento illustra come passare dalla visualizzazione Progettazione XML Schema (Progettazione XSD) all'editor XML. In questo esempio viene utilizzato [lo schema Dell'ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md).

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>Per passare tra le visualizzazioni e l'editor XML

1. Per creare e modificare un nuovo file XML Schema, seguire la procedura descritta in [Procedura: Creare](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)e modificare un file di schema XSD .

2. Per passare a Progettazione XML Schema dall'editor XML, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML **e scegliere Progettazione visualizzazioni**.

3. Per passare alla visualizzazione Graph usando il limite, fare clic sul collegamento Usa la visualizzazione **Graph** per visualizzare la relazione tra i nodi nella visualizzazione iniziale.

4. Trascinare `USAddress` il nodo da XML Schema **Explorer** nella Graph dati. Fare clic con il pulsante destro del mouse sul nodo nella Graph e scegliere Mostra nella visualizzazione `USAddress` **modello di contenuto** nel menu di scelta rapida.

     Viene aperta la visualizzazione modello di contenuto con i dettagli del nodo `USAddress`.

5. Per passare alla visualizzazione iniziale dalla visualizzazione modello di contenuto usando la barra degli strumenti, fare clic sul pulsante **Avvia** visualizzazione sulla barra degli strumenti XSD.

6. Per passare da una visualizzazione all'altra usando i tasti di scelta rapida, premere **CTRL** 1 per la visualizzazione +  iniziale, **CTRL** + **2** per la visualizzazione Graph e CTRL + **3** per la visualizzazione modello di contenuto.

7. Per passare all'editor XML dalla visualizzazione modello di contenuto, fare clic con il pulsante destro del mouse sul nodo e scegliere **Visualizza codice** nel menu di scelta rapida.
