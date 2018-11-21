---
title: Ispezione delle variabili nelle finestre variabili locali e Auto | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b196d993e7091fd9d4b09fe3c228346e7421911e
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257212"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Ispezione delle variabili nelle finestre variabili locali e Auto

Il **Auto** e **variabili locali** finestre mostrano i valori delle variabili durante il debug. Le finestre sono disponibili solo durante una sessione di debug. Il **Auto** finestra Mostra le variabili usate attorno al punto di interruzione corrente. Il **variabili locali** finestra Mostra le variabili definite nell'ambito locale, ovvero in genere la funzione corrente o il metodo. Se questa è la prima volta che si è provato a eseguire il debug di codice, è possibile leggere [scrivere meglio C# di codice usando Visual Studio](../debugger/write-better-code-with-visual-studio.md) e [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md) prima di procedere con questo articolo.

 Il **Auto** è disponibile per la finestra C#, codice di Visual Basic, C++ e Python, ma non per JavaScript o F#.
  
Per aprire la **Auto** finestra durante il debug, selezionare **Debug** > **Windows** > **Auto**, oppure premere **Ctrl**+**Alt**+**V** > **A**.  

Per aprire la **variabili locali** finestra durante il debug, selezionare **Debug** > **Windows** > **variabili locali**, oppure premere **Alt**+**4**.

Se sono necessarie altre informazioni sul debug di base, vedere [Guida introduttiva con il Debugger](../debugger/getting-started-with-the-debugger.md).

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [visualizzazioni dei dati in Visual Studio per Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Utilizzare le finestre Auto e variabili locali

Matrici e oggetti visualizzare nel **Auto** e **variabili locali** windows come controlli ad albero. Selezionare la freccia a sinistra del nome di una variabile per espandere la visualizzazione per mostrare i campi e proprietà. Di seguito è riportato un esempio di un <xref:System.IO.FileStream?displayProperty=fullName> dell'oggetto nel **variabili locali** finestra:

![Variabili locali-FileStream](../debugger/media/locals-filestream.png "variabili locali-FileStream")

Un valore in rosso i **variabili locali** oppure **Auto** finestra significa che il valore è stato modificato dopo l'ultima valutazione. La modifica può derivare da una precedente sessione di debug o perché ne hai modificato il valore nella finestra.

Il formato numerico predefinito nelle finestre del debugger è decimal. Per cambiarlo in esadecimale, fare doppio clic nella **variabili locali** oppure **Auto** finestra e selezionare **visualizzazione esadecimale**. Questa modifica interessa tutte le finestre del debugger.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Modificare i valori delle variabili nella finestra variabili locali o Auto

Per modificare i valori della maggior parte delle variabili nel **Auto** oppure **variabili locali** windows, fare doppio clic su valore e immettere il nuovo valore.

Si può immettere un'espressione al posto di un valore, ad esempio `a + b`. Il debugger accetta la maggior parte delle espressioni di linguaggio valide.

Nel codice C++ nativo potrebbe essere necessario qualificare il contesto di un nome di variabile. Per altre informazioni, vedere [operatore di contesto (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Assicurarsi di che comprendere le conseguenze prima di modificare i valori ed espressioni. Alcuni dei problemi possibili sono:
>
>-   La valutazione di alcune espressioni può comportare la modifica del valore di una variabile o altri effetti sullo stato del programma. Ad esempio, la valutazione `var1 = ++var2` modifica il valore di entrambe `var1` e `var2`. Queste espressioni le seconde esiste [effetti collaterali](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Effetti collaterali può causare risultati imprevisti se non si è necessario tenere in considerazione.
>
>-   La modifica di valori a virgola mobile può causare lievi inesattezze dovute alla conversione dei componenti frazionari da decimali a binari. Anche una modifica apparentemente innocua può comportare modifiche ad alcuni dei bit in una variabile a virgola mobile.

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Modificare il contesto per la finestra variabili locali o Auto

È possibile usare la **posizione di Debug** sulla barra degli strumenti per selezionare una funzione desiderato, thread o processo che modifica il contesto per il **Auto** e **variabili locali** windows.

Per abilitare la **posizione di Debug** sulla barra degli strumenti, fare clic su una parte vuota dell'area della barra degli strumenti e selezionare **posizione di Debug** dall'elenco a discesa o selezione **visualizzazione**  >   **Le barre degli strumenti** > **posizione di Debug**.

Impostare un punto di interruzione e avviare il debug Quando viene raggiunto il punto di interruzione, sospende l'esecuzione ed è possibile visualizzare il percorso nel **posizione di Debug** sulla barra degli strumenti.

![Barra degli strumenti posizione di debug](../debugger/media/debuglocationtoolbar.png "barra degli strumenti posizione di Debug")

## <a name="bkmk_whatvariables"></a> Le variabili nella finestra Auto (C#, C++, Visual Basic, Python)

 Linguaggi di codice differenti vengono visualizzate diverse variabili nel **Auto** finestra.

 - In C# e Visual Basic, il **Auto** finestra Visualizza tutte le variabili usate nella riga corrente o precedente. Ad esempio, in C# o Visual Basic del codice, dichiarare le variabili seguenti quattro:

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

   Impostare un punto di interruzione sulla riga `c = 3;`, e avviare il debugger. Quando l'esecuzione viene sospesa, il **Auto** finestra verrà visualizzato:

   ![Auto-CSharp](../debugger/media/autos-csharp.png "Auto-CSharp")

   Il valore di `c` è 0, perché la riga `c = 3` non è ancora stata eseguita.

 - In C++, il **Auto** finestra Visualizza le variabili usate almeno tre righe prima della riga corrente in cui l'esecuzione viene sospesa. Nel codice C++, ad esempio, dichiarano sei variabili:

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

    Impostare un punto di interruzione sulla riga `e = 5;` ed eseguire il debugger. Quando si arresta l'esecuzione, il **Auto** finestra verrà visualizzato:

    ![Auto-c + +](../debugger/media/autos-cplus.png "Auto-c + +")

    La variabile `e` non è inizializzata, perché la riga `e = 5` non è ancora stata eseguita.

##  <a name="bkmk_returnValue"></a> View return values of method calls
 Nel codice .NET e C++, è possibile esaminare i valori restituiti nel **Auto** finestra quando eseguono istruzioni / o all'esterno di una chiamata al metodo. Chiamata al metodo visualizzazione restituire i valori possono essere utili quando non vengono archiviate in variabili locali. È stato usato un metodo come parametro o come valore restituito di un altro metodo.

 Il seguente, ad esempio, C# codice aggiunge i valori restituiti di due funzioni:

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

Per visualizzare i valori restituiti di `sumVars()` e `subtractVars()` chiamate nella finestra Auto:

1. Impostare un punto di interruzione nella riga `int x = sumVars(a, b) + subtractVars(c, d);` .  
   
1. Avviare il debug e quando si mette in pausa l'esecuzione nel punto di interruzione, selezionare **Esegui istruzione/routine** o premere **F10**. Dovrebbe essere i seguenti valori restituiti nel **Auto** finestra:  
   
  ![Valore restituito di Auto C# ](../debugger/media/autosreturnvaluecsharp2.png "Auto valore restituitoC#")  
  
## <a name="see-also"></a>Vedere anche  
 [Ciò che sta eseguendo il debug?](../debugger/what-is-debugging.md)  
 [Scrivere meglio C# del codice con Visual Studio](../debugger/write-better-code-with-visual-studio.md)  
 [Presentazione di debug](../debugger/debugger-feature-tour.md) [finestre del Debugger](../debugger/debugger-windows.md)
