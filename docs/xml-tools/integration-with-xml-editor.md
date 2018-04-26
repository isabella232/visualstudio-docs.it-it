---
title: Integrazione di progettazione XML Schema con l'Editor XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2e2b7a9e6511faaa1941d65f6b328a07b10f79
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="integration-with-xml-editor"></a>Integrazione con l'editor XML

Progettazione XML Schema è integrato con l'editor XML. Se si modifica un file XSD nell'Editor XML, la modifica verrà riflessa nel [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se si dispone di [visualizzazione grafico](../xml-tools/graph-view.md) o [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) aperto, la modifica si rifletterà anche non esiste. È possibile spostarsi tra Progettazione XML Schema e l'editor XML nei seguenti modi:

-   Nell'Editor XML, fare doppio clic su un nodo e selezionare **Mostra in XML Schema Explorer**.

-   Nella visualizzazione grafico e XML Schema Explorer, fare doppio clic su un nodo, o un nodo e scegliere **Visualizza codice**. Nella visualizzazione modello di contenuto, fare doppio clic su un nodo e selezionare **Visualizza codice**.

Nella schermata seguente è mostrato uno schema XML aperto in XML Schema Explorer. In XML Schema Explorer il set di schemi viene visualizzato con un albero. Nell'editor XML viene visualizzato il testo del nodo attualmente attivo in XML Schema Explorer.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Qualche volta è utile visualizzare il codice nell'editor XML e la finestra di progettazione grafica uno accanto all'altro. Per visualizzare entrambi i file nello stesso momento, fare clic nell'Editor XML e selezionare **Visualizza finestra di progettazione**. Nel menu di finestre di Visual Studio, selezionare **nuovo orizzontali (o verticali) un gruppo di schede**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vedere anche

- [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)