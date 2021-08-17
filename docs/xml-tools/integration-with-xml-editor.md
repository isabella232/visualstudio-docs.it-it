---
title: Integrazione di Progettazione XML Schema con l'editor XML
description: Informazioni sull'integrazione tra Progettazione XML Schema e l'editor XML e sul modo in cui le modifiche apportate in uno vengono riflesse nell'altra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 9ca0996faba3f154799dd9b292e892dfa11e3be7e6b7f86c0f8dceb0bd638160
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423658"
---
# <a name="integration-with-xml-editor"></a>Integrazione con l'editor XML

Progettazione XML Schema è integrato con l'editor XML. Se si modifica un file XSD nell'editor XML, la modifica verrà riflessa in [Xml Schema Explorer.](../xml-tools/xml-schema-explorer.md) Se è aperta la [Graph](../xml-tools/graph-view.md) o [](../xml-tools/content-model-view.md) la visualizzazione modello di contenuto, la modifica verrà riflessa anche in questa finestra. È possibile spostarsi tra Progettazione XML Schema e l'editor XML nei modi seguenti:

- Nell'editor XML fare clic con il pulsante destro del mouse su un nodo e **scegliere Mostra in Xml Schema Explorer**.

- In Visualizzazione Graph xml **schema fare** doppio clic su un nodo oppure fare clic con il pulsante destro del mouse su un nodo e **scegliere Visualizza codice**. Nella visualizzazione modello di contenuto fare clic con il pulsante destro del mouse su un nodo e **scegliere Visualizza codice**.

Lo screenshot seguente mostra un XML Schema aperto in **XML Schema Explorer.** Xml **Schema Explorer visualizza** il set di schemi in una visualizzazione albero. L'editor XML visualizza la visualizzazione testo del nodo attualmente attivo in **ESPLORA XML Schema.**

![Screenshot di un Visual Studio progetto che mostra un nodo XML nel riquadro Editor XML e una visualizzazione albero del set di schemi nel riquadro ESPLORA XML Schema.](../xml-tools/media/xsddesignerwithxmleditor.gif)

In alcuni casi è utile visualizzare il codice nell'editor XML e nella finestra di progettazione grafica affiancata. Per visualizzare entrambi i file contemporaneamente, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML **e scegliere Progettazione visualizzazioni**. Nel menu Visual Studio Windows selezionare Nuovo gruppo di schede **orizzontale (o verticale).**

![Screenshot di un progetto Visual Studio che mostra il riquadro Progettazione visualizzazioni, il riquadro Editor XML e il riquadro Xml Schema Explorer.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vedi anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
