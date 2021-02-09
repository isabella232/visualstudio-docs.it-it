---
title: 'Esaminare le variabili: finestre auto e variabili locali | Microsoft Docs'
description: Controllare le variabili nelle finestre auto e variabili locali durante il debug in Visual Studio. Nelle finestre auto e variabili locali vengono visualizzati i valori delle variabili durante il debug.
ms.custom: SEO-VS-2020, seodec18
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
ms.workload:
- multiple
ms.openlocfilehash: 61378b697b8cf2d50851926bb9f9b64b50878a59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857942"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Esaminare le variabili nelle finestre auto e variabili locali

Nelle finestre **auto** e **variabili locali** vengono visualizzati i valori delle variabili durante il debug. Le finestre sono disponibili solo durante una sessione di debug. La finestra **auto** Mostra le variabili usate intorno al punto di interruzione corrente. La finestra variabili **locali** Mostra le variabili definite nell'ambito locale, che in genere è la funzione o il metodo corrente.

> [!NOTE]
> Se è la prima volta che si tenta di eseguire il debug del codice, è consigliabile leggere il [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) e [tecniche e strumenti di debug](../debugger/write-better-code-with-visual-studio.md) prima di procedere con questo articolo.

 La finestra **auto** è disponibile per il codice C#, Visual Basic, C++ e Python, ma non per JavaScript o F #.

Per aprire la finestra **auto** , durante il debug, selezionare **debug** di  >  **Windows**  >  **auto** oppure premere **CTRL** + **ALT** + **V**  >  **A**.

Per aprire la finestra **variabili locali** , durante il debug, selezionare **debug**  >    >  **variabili locali** di Windows oppure premere **ALT** + **4**.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Usare le finestre auto e variabili locali

Le matrici e gli oggetti vengono visualizzati nelle finestre **auto** e **variabili locali** come controlli struttura ad albero. Selezionare la freccia a sinistra di un nome di variabile per espandere la visualizzazione in modo da visualizzare i campi e le proprietà. Di seguito è riportato un esempio di <xref:System.IO.FileStream?displayProperty=fullName> oggetto nella finestra **variabili locali** :

![Screenshot della finestra variabili locali, con file impostato su un valore System. IO. FileStream.](../debugger/media/locals-filestream.png)

Un valore rosso nella finestra **variabili locali** o **auto** indica che il valore è stato modificato dall'ultima valutazione. La modifica può provenire da una sessione di debug precedente o dal fatto che il valore nella finestra è stato modificato.

Il formato numerico predefinito nelle finestre del debugger è Decimal. Per impostarlo come esadecimale, fare clic con il pulsante destro del mouse nella finestra **variabili locali** o **auto** e selezionare **visualizzazione esadecimale**. Questa modifica ha effetto su tutte le finestre del debugger.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Modificare i valori delle variabili nella finestra auto o variabili locali

Per modificare i valori della maggior parte delle variabili nelle finestre **auto** o variabili **locali** , fare doppio clic sul valore e immettere il nuovo valore.

Si può immettere un'espressione al posto di un valore, ad esempio `a + b`. Il debugger accetta la maggior parte delle espressioni di linguaggio valide.

Nel codice C++ nativo potrebbe essere necessario qualificare il contesto di un nome di variabile. Per altre informazioni, vedere [Context Operator (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Assicurarsi di aver compreso le conseguenze prima di modificare i valori e le espressioni. Di seguito sono riportati alcuni problemi possibili:
>
>- La valutazione di alcune espressioni può comportare la modifica del valore di una variabile o altri effetti sullo stato del programma. Ad esempio, la valutazione `var1 = ++var2` di modifica il valore di `var1` e `var2` . Queste espressioni si dicono avere [effetti collaterali](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Gli effetti collaterali possono provocare risultati imprevisti se non si è a conoscenza di essi.
>
>- La modifica di valori a virgola mobile può causare lievi inesattezze dovute alla conversione dei componenti frazionari da decimali a binari. Anche una modifica apparentemente innocua può causare modifiche ad alcuni bit della variabile a virgola mobile.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Cerca nella finestra auto o variabili locali

È possibile cercare le parole chiave nelle colonne nome, valore e tipo della finestra **auto** o **variabili locali** usando la barra di ricerca sopra ogni finestra. Premere INVIO o selezionare una delle frecce per eseguire una ricerca. Per annullare una ricerca in corso, selezionare l'icona "x" nella barra di ricerca.

Utilizzare le frecce sinistra e destra (MAIUSC + F3 e F3 rispettivamente) per spostarsi tra le corrispondenze trovate.

![Cerca nella finestra variabili locali](../debugger/media/ee-search-locals.png "Cerca nella finestra variabili locali")

Per rendere la ricerca più o meno completa, usare l'elenco a discesa Cerca più a **fondo** nella parte superiore della finestra **auto** o **variabili locali** per selezionare il numero di livelli che si desidera cercare negli oggetti annidati. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Aggiungere le proprietà nella finestra auto o variabili locali

> [!NOTE]
> Questa funzionalità è supportata per .NET Core 3,0 o versione successiva.

È possibile esaminare rapidamente gli oggetti in base alle relative proprietà nelle finestre auto e variabili locali con lo strumento **Proprietà aggiungibili** .  Per usare questo strumento, passare il puntatore del mouse su una proprietà e selezionare l'icona a forma di puntina visualizzata oppure fare clic con il pulsante destro del mouse e selezionare l'opzione **Aggiungi membro come preferito** nel menu di scelta rapida risultante.  Questa operazione consente di eseguire il bubbling della proprietà nella parte superiore dell'elenco delle proprietà dell'oggetto e il nome e il valore della proprietà vengono visualizzati nella colonna **valore** .  Per Rimuovi una proprietà, selezionare di nuovo l'icona del PIN oppure selezionare il **membro Rimuovi come opzione preferita** nel menu di scelta rapida.

![Aggiungere le proprietà nella finestra variabili locali](../debugger/media/basic-pin.gif "Aggiungere le proprietà nella finestra variabili locali")

È anche possibile impostare i nomi delle proprietà e filtrare le proprietà non bloccate quando si visualizza l'elenco delle proprietà dell'oggetto nelle finestre auto o variabili locali.  È possibile accedere a ogni opzione selezionando i pulsanti sulla barra degli strumenti sopra le finestre auto o variabili locali.

![Filtra proprietà preferiti](../debugger/media/filter-pinned-properties-locals.png "Filtra proprietà Preferiti") 
 ![Imposta/Nascondi nomi proprietà](../debugger/media/toggle-property-names.gif "Imposta/Nascondi nomi proprietà")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Modificare il contesto per la finestra auto o variabili locali

È possibile utilizzare la barra degli strumenti **posizione di debug** per selezionare la funzione, il thread o il processo desiderato, che modifica il contesto per le finestre **auto** e **variabili locali** .

Per abilitare la barra degli strumenti **posizione di debug** , fare clic su una parte vuota dell'area della barra degli strumenti, selezionare **posizione di debug** nell'elenco a discesa oppure selezionare **Visualizza** posizione di debug per le  >  **barre degli strumenti**  >  .

Impostare un punto di interruzione e avviare il debug Quando viene raggiunto il punto di interruzione, l'esecuzione viene sospesa ed è possibile visualizzarla nella barra degli strumenti **posizione di debug** .

![Barra degli strumenti posizione di debug](../debugger/media/debuglocationtoolbar.png "Barra degli strumenti Posizione di debug")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Variabili nella finestra auto (C#, C++, Visual Basic, Python)

Diversi linguaggi di codice visualizzano variabili diverse nella finestra **auto** .

- In C# e Visual Basic la finestra **Auto** visualizza tutte le variabili usate nella riga corrente o precedente. Ad esempio, in C# o Visual Basic codice, dichiarare le quattro variabili seguenti:

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

   Impostare un punto di interruzione sulla riga `c = 3;` e avviare il debugger. Quando l'esecuzione viene sospesa, viene visualizzata la finestra **auto** :

   ![Screenshot della finestra auto, con il valore di c impostato su 0.](../debugger/media/autos-csharp.png)

   Il valore di `c` è 0, perché la riga `c = 3` non è stata ancora eseguita.

- In C++ la finestra **auto** Mostra le variabili usate in almeno tre righe prima della riga corrente in cui l'esecuzione viene sospesa. Nel codice C++, ad esempio, dichiarare sei variabili:

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

    Impostare un punto di interruzione sulla riga `e = 5;` ed eseguire il debugger. Quando l'esecuzione viene arrestata, viene visualizzata la finestra **auto** :

    ![Screenshot della finestra auto, con la riga evidenziata che Mostra int c con valore 3.](../debugger/media/autos-cplus.png)

    La variabile `e` non è inizializzata, perché la riga `e = 5` non è stata ancora eseguita.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls
 Nel codice .NET e C++ è possibile esaminare i valori restituiti nella finestra **auto** quando si esegue l'istruzione/routine di una chiamata al metodo. La visualizzazione dei valori restituiti della chiamata al metodo può essere utile quando non vengono archiviati in variabili locali. Un metodo può essere utilizzato come parametro o come valore restituito di un altro metodo.

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

Per visualizzare i valori restituiti delle `sumVars()` chiamate al `subtractVars()` metodo e nella finestra auto:

1. Impostare un punto di interruzione nella riga `int x = sumVars(a, b) + subtractVars(c, d);` .

1. Avviare il debug e quando l'esecuzione viene sospesa in corrispondenza del punto di interruzione, selezionare **Esegui istruzione** /routine o premere **F10**. Nella finestra **auto** vengono visualizzati i valori restituiti seguenti:

  ![Auto valore restituito C #](../debugger/media/autosreturnvaluecsharp2.png "Auto valore restituito C #")

## <a name="see-also"></a>Vedi anche

- [Che cos'è il debug?](../debugger/what-is-debugging.md)
- [Tecniche e strumenti di debug CRT](../debugger/write-better-code-with-visual-studio.md)
- [Esaminare prima di tutto il debug](../debugger/debugger-feature-tour.md)
- [Finestre del debugger](../debugger/debugger-windows.md)
