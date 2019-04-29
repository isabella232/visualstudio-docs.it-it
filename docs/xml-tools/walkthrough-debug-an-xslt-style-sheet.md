---
title: Eseguire il debug di fogli di stile XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808476"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procedura dettagliata: Eseguire il debug di un foglio di stile XSLT

Nei passaggi della procedura dettagliata viene illustrato come usare il debugger XSLT. I passaggi comprendono la visualizzazione delle variabili, l'impostazione dei punti di interruzione e l'esecuzione del codice un'istruzione alla volta. Il debugger consente di eseguire il codice una riga alla volta.

Per prepararsi per questa procedura dettagliata, copiare innanzitutto due [file di esempio](#sample-files) nel computer locale. Uno è il foglio di stile, e uno è il file XML che verrà usato come input per il foglio di stile. In questa procedura dettagliata, il foglio di stile che usiamo Trova tutti i libri il cui costo è inferiore al prezzo medio dei libri.

> [!NOTE]
> Il debugger XSLT è disponibile solo nell'edizione Enterprise di Visual Studio.

## <a name="start-debugging"></a>Avvia debug

1. Dal **File** menu, scegliere **Open** > **File**.

2. Individuare il *seguito average.xsl* del file e scegliere **Open**.

   Il foglio di stile viene aperto nell'editor XML.

3. Fare clic sul pulsante Sfoglia (**...** ) sul **Input** campo della finestra delle proprietà del documento. (Se il **delle proprietà** finestra non è visibile, fare clic sul file aperto nell'editor e quindi scegliere **proprietà**.)

4. Individuare il *books. XML* del file e quindi scegliere **Open**.

   Questo imposta il file di documento di origine che viene usato per la trasformazione XSLT.

5. Impostare una [punto di interruzione](../debugger/using-breakpoints.md) nella riga 12 *seguito average.xsl*. È possibile procedere in uno dei diversi modi:

   - Fare clic sul margine dell'editor nella riga 12.

   - Fare clic su un punto qualsiasi sulla riga 12 e quindi premere **F9**.

   - Fare doppio clic il `xsl:if` tag di inizio e quindi scegliere **punto di interruzione** > **Inserisci punto di interruzione**.

      ![Inserisci punto di interruzione nel file XSL in Visual Studio](media/insert-breakpoint.PNG)

6. Nella barra dei menu, scegliere **XML** > **Avvia debug XSLT** (oppure premere **Alt**+**F5**).

   Avvia il processo di debug.

   Nell'editor, il debugger è posizionato in corrispondenza di `xsl:if` elemento del foglio di stile. Un altro file denominato *seguito average.xml* viene aperto nell'editor; si tratta del file di output che verrà popolato come ogni nodo nel file di input *books. XML* viene elaborato.

   Il **Auto**, **variabili locali**, e **Watch1** finestre vengono visualizzate nella parte inferiore della finestra di Visual Studio. Il **variabili locali** finestra Visualizza tutte le variabili locali e i relativi valori correnti. incluse le variabili definite nel foglio di stile e quelle usate dal debugger per tenere traccia dei nodi presenti nel contesto.

## <a name="watch-window"></a>Finestra Espressioni di controllo

Aggiungiamo, quindi due variabili per il **espressioni di controllo 1** finestra in modo che è possibile esaminare i rispettivi valori durante l'elaborazione del file di input. (È anche possibile usare la **variabili locali** finestra per esaminare i valori se le variabili che si desidera controllare sono già presenti.)

1. Dal **Debug** menu, scegliere **Windows** > **Watch** > **Watch1**.

   Il **espressioni di controllo 1** finestra diventa visibile.

2. Tipo di `$bookAverage` nella **Name** campo e quindi premere **invio**.

   Il valore della `$bookAverage` variabile vengono visualizzate nel **valore** campo.

3. Nella riga successiva, digitare `self::node()` nella **Name** campo e quindi premere **invio**.

   `self::node()` è un'espressione XPath che restituisce il nodo di contesto corrente. Il valore dell'espressione XPath `self::node()` costituisce il primo nodo libro.  Il valore verrà modificato durante le fasi della trasformazione.

4. Espandere la `self::node()` nodo, quindi espandere il nodo che ha valore è `price`.

   ![Finestra Espressioni di controllo durante il debug di XSLT in Visual Studio](media/xslt-debugging-watch-window.png)

   È possibile visualizzare il valore del prezzo del libro per il nodo libro corrente e confrontarla con la `$bookAverage` valore. Poiché il prezzo del libro è inferiore alla media, il `xsl:if` condizione dovrebbe avere esito positivo quando si continua il processo di debug.

## <a name="step-through-the-code"></a>Eseguire il codice

1. Premere **F5** per continuare.

   Poiché il primo nodo libro soddisfatti il `xsl:if` condizione, il nodo libro viene aggiunto per il *seguito average.xml* file di output. Il debugger continua l'esecuzione se non viene posizionato di nuovo sull'elemento `xsl:if` nel foglio di stile. Il debugger è ora posizionato sul secondo nodo libro nel *books. XML* file.

   Nel **Watch1** finestra di `self::node()` cambia di valore nel secondo nodo libro. Analizzando il valore dell'elemento prezzo, è possibile determinare che il prezzo è maggiore del prezzo medio e che pertanto la condizione `xsl:if` non dovrebbe essere eseguita correttamente.

2. Premere **F5** per continuare.

   Poiché il secondo nodo libro non soddisfa il `xsl:if` condizione, il nodo libro non viene aggiunto per il *seguito average.xml* file di output. Il debugger continua l'esecuzione fino a quando non è posizionato nuovamente sul `xsl:if` elemento nel foglio di stile. Il debugger è ora posizionato sul terzo `book` nodo il *books. XML* file.

   Nel **Watch1** finestra di `self::node()` valore viene modificato nel terzo nodo libro. Esaminando il valore della `price` elemento, è possibile determinare che il prezzo è inferiore alla Media. Il `xsl:if` condizione dovrebbe avere esito positivo.

3. Premere **F5** per continuare.

   Perché il `xsl:if` condizione è soddisfatta, il terzo libro viene aggiunto per il *seguito average.xml* file di output. Tutti i libri nel documento XML sono stati elaborati e il debugger si arresta.

## <a name="sample-files"></a>File di esempio

I due file seguenti vengono usati nella procedura dettagliata.

### <a name="below-averagexsl"></a>below-average.xsl

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