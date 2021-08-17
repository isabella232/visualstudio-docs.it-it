---
title: Esaminare le variabili - Finestre Auto e Variabili locali | Microsoft Docs
description: Esaminare le variabili nelle finestre Auto e Variabili locali durante il debug in Visual Studio. Le finestre Auto e Variabili locali mostrano i valori delle variabili durante il debug.
ms.custom: SEO-VS-2020
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 19452ba0473afa55c8ffaef6d852a7a4e08e12f6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081906"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Esaminare le variabili nelle finestre Auto e Variabili locali

Le **finestre Auto e** Variabili locali mostrano **i** valori delle variabili durante il debug. Le finestre sono disponibili solo durante una sessione di debug. La **finestra Auto mostra** le variabili usate intorno al punto di interruzione corrente. La **finestra Variabili** locali mostra le variabili definite nell'ambito locale, che in genere è la funzione o il metodo corrente.

> [!NOTE]
> Se è la prima volta che si prova a eseguire [](../debugger/debugging-absolute-beginners.md) il debug del codice, è possibile leggere Debug per principianti assoluti e Tecniche e strumenti di debug prima di passare a questo articolo. [](../debugger/write-better-code-with-visual-studio.md)

 La **finestra Auto è** disponibile per il codice C#, Visual Basic, C++ e Python, ma non per JavaScript o F#.

Per aprire la **finestra Auto** durante il debug, selezionare  >  **Debug Windows** Auto  >  **o** premere **CTRL** +  +   >  **ALT+A.**

Per aprire la **finestra Variabili** locali durante il debug, selezionare Debug Windows Variabili locali  >    >  oppure **premere** + **ALT+4.**

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Usare le finestre Auto e Variabili locali

Le matrici e gli oggetti vengono visualizzati **nelle finestre Auto e** **Variabili** locali come controlli struttura ad albero. Selezionare la freccia a sinistra del nome di una variabile per espandere la visualizzazione per visualizzare campi e proprietà. Di seguito è riportato un esempio <xref:System.IO.FileStream?displayProperty=fullName> di un oggetto nella **finestra** Variabili locali:

![Screenshot della finestra Variabili locali, con il file impostato su un valore System.IO.FileStream.](../debugger/media/locals-filestream.png)

Un valore rosso nella **finestra Variabili locali** o Auto **indica** che il valore è stato modificato dopo l'ultima valutazione. La modifica potrebbe essere da una sessione di debug precedente o perché il valore nella finestra è stato modificato.

Il formato numerico predefinito nelle finestre del debugger è decimale. Per impostarlo su esadecimale, fare clic  con il pulsante destro del mouse nella finestra Variabili locali o Auto **e** selezionare **Visualizzazione esadecimale**. Questa modifica influisce su tutte le finestre del debugger.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Modificare i valori delle variabili nella finestra Auto o Variabili locali

Per modificare i valori della maggior parte delle variabili **nelle finestre Auto o** **Variabili** locali, fare doppio clic sul valore e immettere il nuovo valore.

Si può immettere un'espressione al posto di un valore, ad esempio `a + b`. Il debugger accetta la maggior parte delle espressioni di linguaggio valide.

Nel codice C++ nativo potrebbe essere necessario qualificare il contesto di un nome di variabile. Per altre informazioni, vedere [Context Operator (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Assicurarsi di comprendere le conseguenze prima di modificare valori ed espressioni. Di seguito sono riportati alcuni possibili problemi:
>
>- La valutazione di alcune espressioni può comportare la modifica del valore di una variabile o altri effetti sullo stato del programma. Ad esempio, la valutazione `var1 = ++var2` modifica il valore di e `var1` `var2` . Queste espressioni hanno effetti [collaterali.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) Gli effetti collaterali possono causare risultati imprevisti se non se ne è a conoscenza.
>
>- La modifica di valori a virgola mobile può causare lievi inesattezze dovute alla conversione dei componenti frazionari da decimali a binari. Anche una modifica apparentemente innocua può comportare modifiche ad alcuni dei bit nella variabile a virgola mobile.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Cercare nella finestra Auto o Variabili locali

È possibile cercare parole chiave nelle colonne Nome,  Valore  e Tipo della finestra Auto o Variabili locali usando la barra di ricerca sopra ogni finestra. Premere INVIO o selezionare una delle frecce per eseguire una ricerca. Per annullare una ricerca in corso, selezionare l'icona "x" nella barra di ricerca.

Usare rispettivamente le frecce sinistra e destra (MAIUSC+F3 e F3) per spostarsi tra le corrispondenze trovate.

![Cerca nella finestra Variabili locali](../debugger/media/ee-search-locals.png "Cerca nella finestra Variabili locali")

Per rendere la ricerca più o  meno completa, usare l'elenco  a discesa Cerca più in profondità nella parte superiore della finestra Auto **o** Variabili locali per selezionare il numero di livelli di profondità in cui eseguire la ricerca negli oggetti annidati. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Aggiungere le proprietà nella finestra Auto o Variabili locali

> [!NOTE]
> Questa funzionalità è supportata per .NET Core 3.0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle relative proprietà nelle finestre Auto e Variabili locali con lo **strumento Proprietà pinnable.**  Per usare questo strumento, passare il puntatore del mouse su una  proprietà e selezionare l'icona della puntina visualizzata oppure fare clic con il pulsante destro del mouse e scegliere l'opzione Aggiungi membro come preferito nel menu di scelta rapida risultante.  Questa proprietà viene visualizzata nella parte superiore dell'elenco delle proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella **colonna** Valore.  Per rimuovere una proprietà, selezionare di nuovo l'icona aggiungi o selezionare l'opzione Rimuovi membro **come** preferito nel menu di scelta rapida.

![Aggiungere le proprietà nella finestra Variabili locali](../debugger/media/basic-pin.gif "Aggiungere le proprietà nella finestra Variabili locali")

È anche possibile attivare o disattivare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto nelle finestre Auto o Variabili locali.  È possibile accedere a ogni opzione selezionando i pulsanti nella barra degli strumenti sopra le finestre Auto o Variabili locali.

![Filtrare le proprietà preferite](../debugger/media/filter-pinned-properties-locals.png "Filtrare le proprietà preferite") 
 ![Attivare/disattivare i nomi delle proprietà](../debugger/media/toggle-property-names.gif "Attivare/disattivare i nomi delle proprietà")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Modificare il contesto per la finestra Auto o Variabili locali

È possibile usare la barra **degli** strumenti Posizione di debug per selezionare una funzione, un thread o un processo desiderato, che modifica il contesto per le **finestre** Auto **e** Variabili locali.

Per abilitare la barra **degli strumenti Percorso** di debug, fare clic in una parte vuota dell'area della barra degli strumenti e selezionare **Percorso** di debug nell'elenco a discesa oppure selezionare **Visualizza** barre degli strumenti Posizione  >    >  **di debug**.

Impostare un punto di interruzione e avviare il debug Quando viene raggiunto il punto di interruzione, l'esecuzione viene sospesa ed è possibile visualizzare il percorso nella barra **degli strumenti Posizione di** debug.

![Barra degli strumenti Percorso di debug](../debugger/media/debuglocationtoolbar.png "Barra degli strumenti Posizione di debug")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a>Variabili nella finestra Auto (C#, C++, Visual Basic, Python)

Linguaggi di codice diversi visualizzano variabili diverse nella **finestra Auto.**

- In C# e Visual Basic la finestra **Auto** visualizza tutte le variabili usate nella riga corrente o precedente. Ad esempio, in C# o Visual Basic codice dichiarare le quattro variabili seguenti:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Impostare un punto di interruzione sulla `c = 3;` riga e avviare il debugger. Quando l'esecuzione viene sospesa, **verrà visualizzata la finestra** Auto:

   ![Screenshot della finestra Auto, con il valore c impostato su 0.](../debugger/media/autos-csharp.png)

   Il valore di `c` è 0, perché la riga `c = 3` non è ancora stata eseguita.

- In C++ la **finestra Auto visualizza** le variabili usate in almeno tre righe prima della riga corrente in cui l'esecuzione viene sospesa. Nel codice C++, ad esempio, dichiarare sei variabili:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Impostare un punto di interruzione sulla riga `e = 5;` ed eseguire il debugger. Quando l'esecuzione viene arrestata, **verrà visualizzata la** finestra Auto:

    ![Screenshot della finestra Auto, con la riga evidenziata che mostra int c con valore 3.](../debugger/media/autos-cplus.png)

    La variabile `e` non è inizializzata perché la riga `e = 5` non è ancora stata eseguita.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls
 Nel codice .NET e C++ è possibile esaminare i valori restituiti nella finestra Auto **quando** si esegue un'istruzione alla volta o all'uscita da una chiamata al metodo. La visualizzazione dei valori restituiti delle chiamate al metodo può essere utile quando non vengono archiviati nelle variabili locali. Un metodo può essere usato come parametro o come valore restituito di un altro metodo.

 Ad esempio, il codice C# seguente aggiunge i valori restituiti di due funzioni:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

Per visualizzare i valori restituiti delle `sumVars()` chiamate al metodo e nella finestra `subtractVars()` Auto:

1. Impostare un punto di interruzione nella riga `int x = sumVars(a, b) + subtractVars(c, d);` .

1. Avviare il debug e, quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, selezionare **Step Over** o premere **F10.** Nella finestra Auto dovrebbero essere visualizzati **i valori restituiti** seguenti:

  ![Il valore restituito automaticamente C #](../debugger/media/autosreturnvaluecsharp2.png "Il valore restituito automaticamente C #")

## <a name="see-also"></a>Vedi anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Prima di tutto esaminare il debug](../debugger/debugger-feature-tour.md)
- [Finestre del debugger](../debugger/debugger-windows.md)
