---
title: Valutare un'espressione XPath durante il debug
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002082"
---
# <a name="evaluate-xpath-expressions"></a>Valutare le espressioni XPath

È possibile valutare le espressioni XPath tramite i **controllo immediato** finestra durante il debug. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente (vale a dire, il `self::node()` nodo il **variabili locali** finestra) fornisce il contesto di valutazione per l'espressione XPath.

Quando si valuta un'espressione XPath:

- Sono supportate le funzioni XPath incorporate.

- Non sono supportate le funzioni XSLT incorporate e funzioni definite dall'utente.

> [!NOTE]
> Debug XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Valutare un'espressione XPath

La procedura seguente usa il *seguito average.xsl* e *books. XML* dei file dal [procedura dettagliata: Eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) pagina.

1. Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.

2. Per avviare il debug, scegli **XML** > **Avvia debug XSLT** sulla barra dei menu (oppure premere **Alt**+**F5** ).

   Il debugger viene avviato e interrotto sul tag `xsl:if`.

3. Fare doppio clic e selezionare **controllo immediato**.

   Il **controllo immediato** verrà visualizzata la finestra.

4. Immettere `./price/text()` nella **espressione** campo il **controllo immediato** finestra di dialogo casella e quindi scegliere **Rivaluta**.

   Il prezzo del nodo libro corrente viene visualizzato nei **valore** casella.

   ![Valutare un'espressione XPath nella finestra controllo immediato](media/quickwatch-price.png)

5. Modificare l'espressione XPath `./price/text() < $bookAverage` e fare clic su **Rivaluta**.

   Il **valore** casella Mostra che l'espressione XPath restituisce `true`.

## <a name="see-also"></a>Vedere anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)