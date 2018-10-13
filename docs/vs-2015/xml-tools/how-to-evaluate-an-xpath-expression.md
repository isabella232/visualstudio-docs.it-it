---
title: "Procedura: valutare un'espressione XPath | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05758034c0228f0efd7fb3ae63bd3b7e0d5e3095
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210431"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procedura: valutare un'espressione XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile valutare le espressioni XPath con il **controllo immediato** nella finestra di dialogo. L'espressione XPath deve essere valida in base alla raccomandazione W3C XPath 1.0 (informazioni in lingua inglese). Il contesto XSLT corrente, ovvero, ovvero il `self::node()` nodo il **variabili locali** finestra, fornisce il contesto di valutazione per l'espressione XPath.  
  
 Nell'elenco seguente vengono descritte le funzioni supportate durante la valutazione di un'espressione XPath:  
  
-   Sono supportate le funzioni XPath incorporate.  
  
-   Non sono supportate le funzioni XSLT incorporate.  
  
-   Non sono supportate le funzioni definite dall'utente.  
  
> [!NOTE]
>  La procedura seguente usa i file belowAvg. xsl e books. XML dal [procedura dettagliata: eseguire il Debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) argomento.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Per valutare un'espressione XPath  
  
1.  Inserire un punto di interruzione in corrispondenza del tag di inizio `xsl:if`.  
  
2.  Scegliere il **Debug XSLT** pulsante sulla barra degli strumenti Editor XML.  
  
     Il debugger viene avviato e interrotto sul tag `xsl:if`.  
  
3.  Fare doppio clic e selezionare **controllo immediato**.  
  
     Il **controllo immediato** verrà visualizzata la finestra di dialogo.  
  
4.  Immettere `./price/text()` nella **espressione** campo il **controllo immediato** nella finestra di dialogo e fare clic su **Rivaluta**.  
  
     Il prezzo del nodo libro corrente viene visualizzato nei **valore** casella.  
  
5.  Modificare l'espressione XPath `./price/text() < $bookAverage` e fare clic su **Rivaluta**.  
  
     Il **valore** casella Mostra che l'espressione XPath restituisce `true`.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)

