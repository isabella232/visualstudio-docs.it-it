---
title: Debug di fogli di stile XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410116"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procedura dettagliata: eseguire il debug di un foglio di stile XSLT

Nei passaggi della procedura dettagliata viene illustrato come usare il debugger XSLT. I passaggi comprendono la visualizzazione delle variabili, l'impostazione dei punti di interruzione e l'esecuzione del codice un'istruzione alla volta. Il debugger consente di eseguire il codice una riga alla volta.

Per preparare questa procedura dettagliata, copiare prima i due [file di esempio](#sample-files) nel computer locale. Uno è il foglio di stile e uno è il file XML che verrà usato come input per il foglio di stile. In questa procedura dettagliata, il foglio di stile usato trova tutti i libri il cui costo è inferiore al prezzo medio del libro.

> [!NOTE]
> Il debugger XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="start-debugging"></a>Consente di iniziare il debug

1. Scegliere **apri** > **file**dal menu **file** .

2. Individuare il file *below-average. xsl* e scegliere **Apri**.

   Il foglio di stile verrà aperto nell'editor XML.

3. Fare clic sul pulsante Sfoglia ( **...** ) nel campo di **input** della finestra proprietà del documento. Se la finestra **Proprietà** non è visibile, fare clic con il pulsante destro del mouse in un punto qualsiasi del file aperto nell'editor, quindi scegliere **Proprietà**.

4. Individuare il file *books. XML* , quindi scegliere **Apri**.

   Viene impostato il file del documento di origine utilizzato per la trasformazione XSLT.

5. Impostare un punto di [interruzione](../debugger/using-breakpoints.md) nella riga 12 di *below-average. xsl*. Questa operazione può essere eseguita in uno dei modi seguenti:

   - Fare clic sul margine dell'editor sulla riga 12.

   - Fare clic in un punto qualsiasi della riga 12, quindi premere **F9**.

   - Fare clic con il pulsante destro del mouse sul tag di inizio `xsl:if` e scegliere punto di **interruzione** > Inserisci punto di **interruzione**.

      ![Inserisci punto di interruzione nel file XSL in Visual Studio](media/insert-breakpoint.PNG)

6. Nella barra dei menu scegliere **XML** > **avviare il debug XSLT** oppure premere **ALT**+**F5**.

   Viene avviato il processo di debug.

   Nell'editor il debugger è posizionato sull'elemento `xsl:if` del foglio di stile. Un altro file denominato *below-average. XML* verrà aperto nell'editor; si tratta del file di output che verrà popolato quando viene elaborato ogni nodo nel file di input *books. XML* .

   Le finestre **auto**, **variabili locali**e **espressioni di controllo 1** vengono visualizzate nella parte inferiore della finestra di Visual Studio. Nella finestra variabili **locali** vengono visualizzate tutte le variabili locali e i relativi valori correnti. incluse le variabili definite nel foglio di stile e quelle usate dal debugger per tenere traccia dei nodi presenti nel contesto.

## <a name="watch-window"></a>Finestra di controllo

Verranno aggiunte due variabili alla finestra espressione di **controllo 1** , in modo che sia possibile esaminarne i valori durante l'elaborazione del file di input. È anche possibile usare la finestra variabili **locali** per esaminare i valori se le variabili che si vuole controllare sono già presenti.

1. Dal menu **debug** scegliere **Windows** > **Watch** > espressione di **controllo 1**.

   La finestra espressione di **controllo 1** diventa visibile.

2. Digitare `$bookAverage` nel campo **nome** , quindi premere **invio**.

   Il valore della variabile `$bookAverage` viene visualizzato nel campo **valore** .

3. Nella riga successiva digitare `self::node()` nel campo **nome** , quindi premere **invio**.

   `self::node()` è un'espressione XPath che restituisce il nodo di contesto corrente. Il valore dell'espressione XPath `self::node()` costituisce il primo nodo libro. Il valore verrà modificato durante le fasi della trasformazione.

4. Espandere il nodo `self::node()`, quindi espandere il nodo il cui valore è `price`.

   ![finestra Espressioni di controllo durante il debug XSLT in Visual Studio](media/xslt-debugging-watch-window.png)

   È possibile visualizzare il valore del prezzo del libro per il nodo book corrente e confrontarlo con il valore `$bookAverage`. Poiché il prezzo del libro è inferiore alla media, la condizione `xsl:if` dovrebbe avere esito positivo quando si continua il processo di debug.

## <a name="step-through-the-code"></a>Eseguire il codice un'istruzione alla volta

1. Premere **F5** per continuare.

   Poiché il nodo del primo libro ha soddisfatto la condizione `xsl:if`, il nodo libro viene aggiunto al file di output *below-average. XML* . Il debugger continua l'esecuzione se non viene posizionato di nuovo sull'elemento `xsl:if` nel foglio di stile. Il debugger è ora posizionato sul secondo nodo libro nel file *books. XML* .

   Nella finestra espressione di **controllo 1** , il valore `self::node()` diventa il secondo nodo libro. Analizzando il valore dell'elemento prezzo, è possibile determinare che il prezzo è maggiore del prezzo medio e che pertanto la condizione `xsl:if` non dovrebbe essere eseguita correttamente.

2. Premere **F5** per continuare.

   Poiché il secondo nodo libro non soddisfa la condizione di `xsl:if`, il nodo libro non viene aggiunto al file di output *below-average. XML* . Il debugger continua a essere eseguito fino a quando non viene posizionato nuovamente sull'elemento `xsl:if` nel foglio di stile. Il debugger è ora posizionato sul terzo nodo `book` nel file *books. XML* .

   Nella finestra espressione di **controllo 1** , il valore `self::node()` viene modificato nel terzo nodo libro. Esaminando il valore dell'elemento `price`, è possibile determinare che il prezzo è inferiore alla media. La condizione `xsl:if` dovrebbe avere esito positivo.

3. Premere **F5** per continuare.

   Poiché la condizione `xsl:if` è stata soddisfatta, il terzo libro viene aggiunto al file di output *below-average. XML* . Tutti i libri nel documento XML sono stati elaborati e il debugger si arresta.

## <a name="sample-files"></a>File di esempio

I due file seguenti vengono usati nella procedura dettagliata.

### <a name="below-averagexsl"></a>below-average. Xsl

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
