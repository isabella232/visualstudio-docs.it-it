---
title: "Procedura: valutare un'espressione XPath | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670872"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procedura: valutare un'espressione XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile valutare le espressioni XPath con la finestra di dialogo controllo **immediato** . L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, ovvero il `self::node()` nodo nella finestra **variabili locali** , fornisce il contesto di valutazione per l'espressione XPath.

 Nell'elenco seguente vengono descritte le funzioni supportate durante la valutazione di un'espressione XPath:

- Sono supportate le funzioni XPath incorporate.

- Non sono supportate le funzioni XSLT incorporate.

- Non sono supportate le funzioni definite dall'utente.

> [!NOTE]
> La procedura seguente usa i file file belowAvg. xsl e books.xml dell'argomento [scenario: debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Per valutare un'espressione XPath

1. Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.

2. Fare clic sul pulsante **debug XSL** sulla barra degli strumenti dell'editor XML.

     Il debugger viene avviato e interrotto sul tag `xsl:if`.

3. Fare clic con il pulsante destro del mouse e scegliere **immediato**.

     Verrà visualizzata la finestra di dialogo controllo **immediato** .

4. Immettere `./price/text()` nel campo **espressione** della finestra di dialogo controllo **immediato** e fare clic su **Rivaluta**.

     Il prezzo del nodo libro corrente viene visualizzato nella casella **valore** .

5. Modificare l'espressione XPath in `./price/text() < $bookAverage` e fare clic su **Rivaluta**.

     Nella casella **valore** viene indicato che l'espressione XPath restituisce `true` .

## <a name="see-also"></a>Vedere anche
 [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
