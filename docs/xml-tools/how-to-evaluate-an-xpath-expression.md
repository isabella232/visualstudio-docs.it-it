---
title: Valutare un'espressione XPath durante il debug
ms.date: 03/05/2019
description: Informazioni su come valutare le espressioni XPath usando la finestra Controllo immediato durante il debug.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: a5d229bc035edcb3460ca57050ddfd1988d94587
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710534"
---
# <a name="evaluate-xpath-expressions"></a>Valutare le espressioni XPath

È possibile valutare le espressioni XPath usando la **finestra Controllo** immediato durante il debug. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, ovvero il nodo nella finestra Variabili locali, fornisce il contesto di valutazione `self::node()` per l'espressione  XPath.

Quando si valuta un'espressione XPath:

- Sono supportate le funzioni XPath incorporate.

- Le funzioni XSLT predefinite e le funzioni definite dall'utente non sono supportate.

> [!NOTE]
> Il debug XSLT è disponibile solo nell'Enterprise di Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Valutare un'espressione XPath

La procedura seguente usa i *file below-average.xsl* *ebooks.xml* dalla pagina Procedura dettagliata: Eseguire il debug di un foglio di stile [XSLT.](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files)

1. Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.

2. Per avviare il debug, **scegliere XML** Avvia  >  **debug XSLT** sulla barra dei menu (oppure premere **ALT** + **F5).**

   Il debugger viene avviato e interrotto sul tag `xsl:if`.

3. Fare clic con il pulsante destro del mouse **e scegliere Controllo immediato.**

   Verrà **visualizzata la finestra** Controllo immediato.

4. Immettere `./price/text()` nel campo **Espressione** della finestra **di dialogo** Controllo immediato e quindi scegliere **Rivaluta**.

   Il prezzo del nodo libro corrente viene visualizzato nella **casella** Valore .

   ![Valutare un'espressione XPath nella finestra Controllo immediato](media/quickwatch-price.png)

5. Modificare l'espressione XPath in `./price/text() < $bookAverage` e fare clic su **Rivaluta**.

   La **casella Valore** indica che l'espressione XPath restituisce `true` .

## <a name="see-also"></a>Vedi anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
