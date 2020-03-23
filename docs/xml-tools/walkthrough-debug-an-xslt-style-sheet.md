---
title: Eseguire il debug dei fogli di stile XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301720"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procedura dettagliata: debug di un foglio di stile XSLTWalkthrough: Debug an XSLT style sheet

Nei passaggi della procedura dettagliata viene illustrato come usare il debugger XSLT. I passaggi comprendono la visualizzazione delle variabili, l'impostazione dei punti di interruzione e l'esecuzione del codice un'istruzione alla volta. Il debugger consente di eseguire il codice una riga alla volta.

Per preparare questa procedura dettagliata, copiare innanzitutto i due [file di esempio](#sample-files) nel computer locale. Uno è il foglio di stile, e uno è il file XML che useremo come input per il foglio di stile. In questa procedura dettagliata, il foglio di stile utilizzato consente di trovare tutti i libri il cui costo è inferiore al prezzo medio del libro.

> [!NOTE]
> Il debugger XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="start-debugging"></a>Consente di iniziare il debug

1. Scegliere **Apri** > **file**dal menu **File** .

2. Individuare il file *below-average.xsl* e scegliere **Apri**.

   Il foglio di stile viene aperto nell'editor XML.

3. Fare clic sul pulsante Sfoglia (**...**) nel campo **Input** della finestra delle proprietà del documento. Se la finestra **Proprietà** non è visibile, fare clic con il pulsante destro del mouse in un punto qualsiasi del file aperto nell'editor, quindi scegliere **Proprietà.**

4. Individuare il file *books.xml* e quindi scegliere **Apri**.

   In questo modo viene impostato il file del documento di origine utilizzato per la trasformazione XSLT.

5. Impostare un [punto di interruzione](../debugger/using-breakpoints.md) nella riga 12 di *below-average.xsl*. È possibile eseguire questa operazione in uno dei diversi modi seguenti:You can do this in one of multiple ways:

   - Fare clic sul margine dell'editor alla riga 12.

   - Fare clic in un punto qualsiasi della riga 12 e quindi premere **F9**.

   - Fare clic `xsl:if` con il pulsante destro del mouse sul tag di inizio, quindi scegliere**Inserisci punto di** **interruzione** > .

      ![Inserire un punto di interruzione nel file XSL in Visual StudioInsert breakpoint in XSL file in Visual Studio](media/insert-breakpoint.PNG)

6. Sulla barra dei menu scegliere **Avvio** > **XML debugging XSLT** (oppure premere **ALT**+**F5**).

   Viene avviato il processo di debug.

   Nell'editor, il debugger è `xsl:if` posizionato sull'elemento del foglio di stile. Nell'editor viene aperto un altro file denominato *below-average.xml;* questo è il file di output che verrà popolato quando ogni nodo nel file di input *books.xml* viene elaborato.

   Le finestre **Auto**, **Variabili locali**ed Espressioni di **controllo 1** vengono visualizzate nella parte inferiore della finestra di Visual Studio. Nella finestra **Variabili locali** vengono visualizzate tutte le variabili locali e i relativi valori correnti. incluse le variabili definite nel foglio di stile e quelle usate dal debugger per tenere traccia dei nodi presenti nel contesto.

## <a name="watch-window"></a>Finestra Espressioni di controllo

Aggiungeremo due variabili alla finestra **Espressioni di controllo 1** in modo da poter esaminare i relativi valori durante l'elaborazione del file di input. È inoltre possibile utilizzare la finestra **Variabili locali** per esaminare i valori se le variabili che si desidera controllare sono già presenti.

1. Scegliere **Windows** > **Watch** > **1**dal menu **Debug** .

   La finestra **Espressioni di controllo 1** diventa visibile.

2. Digitare `$bookAverage` nel campo **Nome** e quindi premere **INVIO**.

   Il valore `$bookAverage` della variabile viene visualizzato nel campo **Valore.**

3. Nella riga successiva `self::node()` digitare nel campo **Nome** e quindi premere **INVIO.**

   `self::node()`è un'espressione XPath che restituisce il nodo di contesto corrente. Il valore dell'espressione XPath `self::node()` costituisce il primo nodo libro.  Il valore verrà modificato durante le fasi della trasformazione.

4. Espandere `self::node()` il nodo e quindi espandere il `price`nodo il valore è .

   ![Finestra Espressioni di controllo durante il debug XSLT in Visual Studio](media/xslt-debugging-watch-window.png)

   È possibile visualizzare il valore del prezzo contabile per `$bookAverage` il nodo libro corrente e confrontarlo con il valore. Poiché il prezzo del libro `xsl:if` è inferiore alla media, la condizione dovrebbe avere esito positivo quando si continua il processo di debug.

## <a name="step-through-the-code"></a>Eseguire il codice un'istruzione alla volta

1. Premere **F5** per continuare.

   Poiché il primo `xsl:if` nodo book ha soddisfatto la condizione, il nodo book viene aggiunto al file di output *below-average.xml.* Il debugger continua l'esecuzione se non viene posizionato di nuovo sull'elemento `xsl:if` nel foglio di stile. Il debugger è ora posizionato sul secondo nodo book nel file *books.xml.*

   Nella finestra Espressione di `self::node()` controllo **1,** il valore viene modificato nel secondo nodo libro. Analizzando il valore dell'elemento prezzo, è possibile determinare che il prezzo è maggiore del prezzo medio e che pertanto la condizione `xsl:if` non dovrebbe essere eseguita correttamente.

2. Premere **F5** per continuare.

   Poiché il secondo nodo `xsl:if` book non soddisfa la condizione, il nodo book non viene aggiunto al file di output *below-average.xml.* Il debugger continua a essere eseguito fino `xsl:if` a quando non viene posizionato nuovamente sull'elemento nel foglio di stile. Il debugger è ora posizionato `book` sul terzo nodo nel file *books.xml.*

   Nella finestra Espressione di `self::node()` controllo **1,** il valore viene modificato nel terzo nodo libro. Esaminando il valore `price` dell'elemento, è possibile determinare che il prezzo è inferiore alla media. La `xsl:if` condizione dovrebbe avere esito positivo.

3. Premere **F5** per continuare.

   Poiché `xsl:if` la condizione è stata soddisfatta, il terzo libro viene aggiunto al file di output *below-average.xml.* Tutti i libri nel documento XML sono stati elaborati e il debugger si arresta.

## <a name="sample-files"></a>File di esempio

I due file seguenti vengono usati nella procedura dettagliata.

### <a name="below-averagexsl"></a>sotto la media.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price &lt; $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>books.xml

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Vedere anche

- [Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)](../xml-tools/debugging-xslt.md)
