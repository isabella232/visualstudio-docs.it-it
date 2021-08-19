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
ms.openlocfilehash: 03b26b7fb9ee44cefe21c92b34c0a35830d63d0b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098723"
---
# <a name="integration-with-xml-editor"></a>Integrazione con l'editor XML

Progettazione XML Schema è integrato con l'editor XML. Se si modifica un file XSD nell'editor XML, la modifica verrà riflessa in [XML Schema Explorer.](../xml-tools/xml-schema-explorer.md) Se è aperta la [Graph](../xml-tools/graph-view.md) o [](../xml-tools/content-model-view.md) la visualizzazione modello di contenuto, la modifica verrà riflessa anche in questa finestra. È possibile spostarsi tra Progettazione XML Schema e l'editor XML nei modi seguenti:

- Nell'editor XML fare clic con il pulsante destro del mouse su un nodo e **scegliere Mostra in Xml Schema Explorer**.

- Nella visualizzazione Graph xml **schema fare** doppio clic su un nodo oppure fare clic con il pulsante destro del mouse su un nodo e **scegliere Visualizza codice**. Nella visualizzazione modello di contenuto fare clic con il pulsante destro del mouse su un nodo e **scegliere Visualizza codice**.

Lo screenshot seguente mostra un XML Schema aperto in **XML Schema Explorer.** Xml **Schema Explorer visualizza** il set di schemi in una visualizzazione albero. L'editor XML visualizza la visualizzazione testo del nodo attualmente attivo in **ESPLORA XML Schema.**

![Screenshot di un progetto Visual Studio che mostra un nodo XML nel riquadro Editor XML e una visualizzazione albero del set di schemi nel riquadro Esplora XML Schema.](../xml-tools/media/xsddesignerwithxmleditor.gif)

In alcuni casi è utile visualizzare il codice nell'editor XML e nella finestra di progettazione grafica affiancata. Per visualizzare entrambi i file contemporaneamente, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML **e scegliere Progettazione visualizzazioni**. Nel menu Visual Studio Windows nuovo gruppo di schede **orizzontale (o verticale).**

![Screenshot di un progetto Visual Studio che mostra il riquadro Progettazione visualizzazioni, il riquadro Editor XML e il riquadro Esplora XML Schema.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vedi anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
