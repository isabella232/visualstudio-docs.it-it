---
title: Integrazione di progettazione XML Schema con l'editor XML
description: Vengono fornite informazioni sull'integrazione tra progettazione XML Schema e l'editor XML e sul modo in cui le modifiche apportate in uno di essi si riflettono nell'altro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9569e33f8f9f861bc5d89030c6fe38b0ab853a6f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400187"
---
# <a name="integration-with-xml-editor"></a>Integrazione con l'editor XML

Progettazione XML Schema è integrato con l'editor XML. Se si modifica un file XSD nell'editor XML, la modifica viene riflessa in [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se è aperta la [visualizzazione grafico](../xml-tools/graph-view.md) o la [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) , la modifica verrà riflessa anche in questa posizione. È possibile spostarsi tra progettazione XML Schema e l'editor XML nei modi seguenti:

- Nell'editor XML, fare clic con il pulsante destro del mouse su un nodo e selezionare **Mostra in XML Schema Explorer**.

- Nella visualizzazione grafico e in **XML Schema Explorer** fare doppio clic su un nodo oppure fare clic con il pulsante destro del mouse su un nodo e selezionare **Visualizza codice**. Nella visualizzazione modello di contenuto, fare clic con il pulsante destro del mouse su un nodo e selezionare **Visualizza codice**.

Nella schermata seguente viene illustrato un XML schema aperto in **XML Schema Explorer**. In **XML Schema Explorer** viene visualizzato il set di schemi in una visualizzazione struttura ad albero. Nell'editor XML viene visualizzata la visualizzazione di testo del nodo attualmente attivo in **XML Schema Explorer**.

![Screenshot di un progetto di Visual Studio che mostra un nodo XML nel riquadro dell'editor XML e una visualizzazione albero del set di schemi nel riquadro XML Schema Explorer.](../xml-tools/media/xsddesignerwithxmleditor.gif)

A volte è utile visualizzare il codice nell'editor XML e la finestra di progettazione grafica affiancata. Per visualizzare entrambi i file nello stesso momento, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML e scegliere **Visualizza finestra di progettazione**. Nel menu Windows di Visual Studio selezionare **nuovo gruppo di schede orizzontale (o verticale)**.

![Screenshot di un progetto di Visual Studio che mostra il riquadro Progettazione viste, il riquadro Editor XML e il riquadro XML Schema Explorer.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
