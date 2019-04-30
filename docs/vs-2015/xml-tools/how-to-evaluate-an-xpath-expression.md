---
title: "Procedura: Valutare un'espressione XPath | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03c43d272d3c740c55314db5d1b7b6c225b7e5c8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421767"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procedura: di un'espressione XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile valutare le espressioni XPath con il **controllo immediato** nella finestra di dialogo. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, ovvero, ovvero il `self::node()` nodo il **variabili locali** finestra, fornisce il contesto di valutazione per l'espressione XPath.  
  
 Nell'elenco seguente vengono descritte le funzioni supportate durante la valutazione di un'espressione XPath:  
  
- Sono supportate le funzioni XPath incorporate.  
  
- Non sono supportate le funzioni XSLT incorporate.  
  
- Non sono supportate le funzioni definite dall'utente.  
  
> [!NOTE]
> La procedura seguente usa i file belowAvg. xsl e books. XML dal [procedura dettagliata: Eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) argomento.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Per valutare un'espressione XPath  
  
1. Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.  
  
2. Scegliere il **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
     Il debugger viene avviato e interrotto sul tag `xsl:if`.  
  
3. Fare doppio clic e selezionare **controllo immediato**.  
  
     Il **controllo immediato** verrà visualizzata la finestra di dialogo.  
  
4. Immettere `./price/text()` nella **espressione** campo il **controllo immediato** nella finestra di dialogo e fare clic su **Rivaluta**.  
  
     Il prezzo del nodo libro corrente viene visualizzato nei **valore** casella.  
  
5. Modificare l'espressione XPath `./price/text() < $bookAverage` e fare clic su **Rivaluta**.  
  
     Il **valore** casella Mostra che l'espressione XPath restituisce `true`.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
