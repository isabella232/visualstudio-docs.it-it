---
title: "Procedura: valutare un'espressione XPath"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02492f2e1760df3ce5cd6751808303bae75577e2
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procedura: valutare un'espressione XPath

È possibile valutare le espressioni XPath tramite i **controllo immediato** la finestra di dialogo. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, vale a dire il `self::node()` nodo nel **variabili locali** finestra: fornisce il contesto di valutazione per l'espressione XPath.

 Nell'elenco seguente vengono descritte le funzioni supportate durante la valutazione di un'espressione XPath:

-   Sono supportate le funzioni XPath incorporate.

-   Non sono supportate le funzioni XSLT incorporate.

-   Non sono supportate le funzioni definite dall'utente.

> [!NOTE]
> La procedura seguente usa il *belowAvg* e *Books* i file dal [procedura dettagliata: eseguire il Debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) argomento.

## <a name="to-evaluate-an-xpath-expression"></a>Per valutare un'espressione XPath

1.  Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.

2.  Fare clic su di **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.

     Il debugger viene avviato e interrotto sul tag `xsl:if`.

3.  Mouse e scegliere **controllo immediato**.

     Il **controllo immediato** viene visualizzata la finestra di dialogo.

4.  Immettere `./price/text()` nel **espressione** campo il **controllo immediato** la finestra di dialogo e fare clic su **Rivaluta**.

     Il prezzo del nodo libro corrente viene visualizzato nel **valore** casella.

5.  Modificare l'espressione XPath in `./price/text() < $bookAverage` e fare clic su **Rivaluta**.

     Il **valore** mostra che l'espressione XPath restituisce `true`.

## <a name="see-also"></a>Vedere anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)