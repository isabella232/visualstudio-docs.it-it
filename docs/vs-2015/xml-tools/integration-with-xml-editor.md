---
title: Integrazione con l'editor XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c0d1088e9932613466209ef8517ac5035c0b613
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656246"
---
# <a name="integration-with-xml-editor"></a>Integrazione con l'editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Progettazione XML Schema è integrato con l'editor XML. Se si modifica un file XSD nell'editor XML, la modifica viene riflessa in [XML Schema Explorer](../xml-tools/xml-schema-explorer.md). Se è aperta la [visualizzazione grafico](../xml-tools/graph-view.md) o la [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) , la modifica verrà riflessa anche in questa posizione. È possibile spostarsi tra Progettazione XML Schema e l'editor XML nei seguenti modi:

- Nell'editor XML, fare clic con il pulsante destro del mouse su un nodo e selezionare **Mostra in XML Schema Explorer**.

- Nella visualizzazione grafico e in XML Schema Explorer fare doppio clic su un nodo oppure fare clic con il pulsante destro del mouse su un nodo e selezionare **Visualizza codice**. Nella visualizzazione modello di contenuto, fare clic con il pulsante destro del mouse su un nodo e selezionare **Visualizza codice**.

  Nella schermata seguente è mostrato uno schema XML aperto in XML Schema Explorer. In XML Schema Explorer il set di schemi viene visualizzato con un albero. Nell'editor XML viene visualizzato il testo del nodo attualmente attivo in XML Schema Explorer.

  ![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")

  Qualche volta è utile visualizzare il codice nell'editor XML e la finestra di progettazione grafica uno accanto all'altro. Per visualizzare entrambi i file nello stesso momento, fare clic con il pulsante destro del mouse in un punto qualsiasi dell'editor XML e scegliere **Visualizza finestra di progettazione**. Nel menu Windows di Visual Studio selezionare **nuovo gruppo di schede orizzontale (o verticale)** .

  ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")

## <a name="see-also"></a>Vedere anche
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)
