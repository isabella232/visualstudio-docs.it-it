---
title: Valutare un'espressione XPath durante il debug
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 523c89af70c762f0cd0e31519c8c862c440c79eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654278"
---
# <a name="evaluate-xpath-expressions"></a>Valutare le espressioni XPath

È possibile valutare le espressioni XPath usando la finestra controllo **immediato** durante il debug. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, ovvero il nodo `self::node()` nella finestra **variabili locali** , fornisce il contesto di valutazione per l'espressione XPath.

Quando si valuta un'espressione XPath:

- Sono supportate le funzioni XPath incorporate.

- Le funzioni XSLT predefinite e le funzioni definite dall'utente non sono supportate.

> [!NOTE]
> Il debug XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Valutare un'espressione XPath

Nella procedura seguente vengono usati i file *below-average. xsl* e *books. XML* della pagina [procedura dettagliata: debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) .

1. Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.

2. Per avviare il debug, scegliere **XML**  > **avviare il debug XSLT** sulla barra dei menu oppure premere **ALT** +**F5**.

   Il debugger viene avviato e interrotto sul tag `xsl:if`.

3. Fare clic con il pulsante destro del mouse e scegliere **immediato**.

   Verrà visualizzata la finestra controllo **immediato** .

4. Immettere `./price/text()` nel campo **espressione** della finestra di dialogo controllo **immediato** , quindi scegliere **Rivaluta**.

   Il prezzo del nodo libro corrente viene visualizzato nella casella **valore** .

   ![Valutare un'espressione XPath nella finestra controllo immediato](media/quickwatch-price.png)

5. Modificare l'espressione XPath in `./price/text() < $bookAverage` e fare clic su **Rivaluta**.

   Nella casella **valore** viene indicato che l'espressione XPath restituisce `true`.

## <a name="see-also"></a>Vedere anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)