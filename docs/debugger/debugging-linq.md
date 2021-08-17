---
title: Debug di linq | Microsoft Docs
description: Eseguire il debug di LINQ (Language Integrated Query) in Visual Studio. Visualizzare i risultati LINQ. Informazioni sulle differenze di comportamento durante l'esecuzione di istruzioni nel codice LINQ.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c5391d9784324931cbb9d58b53e10722324c3efc9ebe82526b389786aecd49d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420340"
---
# <a name="debugging-linq"></a>Debug di LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supporta il debug di codice LINQ (Language Integrated Query), con alcune limitazioni. La maggior parte delle funzionalità di debug è compatibile con le istruzioni LINQ, inclusa l'esecuzione di istruzioni, l'impostazione di punti di interruzione e la visualizzazione dei risultati nelle finestre del debugger. In questo argomento vengono descritte le principali limitazioni del debug di codice LINQ.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a>Visualizzazione dei risultati LINQ
 È possibile visualizzare il risultato di un'istruzione LINQ usando i suggerimenti dati, la finestra Espressioni di controllo e la finestra di dialogo Controllo immediato. Quando si usa una finestra di origine, passare con il puntatore su una query nella finestra di origine per visualizzare un suggerimento dati. È possibile copiare una variabile LINQ e incollarla nella finestra Espressioni di controllo o nella finestra di dialogo Controllo immediato.

 In LINQ, le query non vengono valutate al momento della creazione o della dichiarazione, ma soltanto al momento dell'uso. La query non dispone pertanto di un valore fino a quando non viene valutata. Per una descrizione completa della creazione e della valutazione delle query, vedere Introduzione alle query [LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) o [Scrittura della prima query LINQ.](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query)

 Per visualizzare il risultato di una query, è necessario che venga valutata dal debugger. Tenere presenti alcuni effetti della valutazione implicita, che avviene quando si visualizza il risultato di una query LINQ nel debugger:

- La singola valutazione della query e l'espansione del nodo dei risultati richiedono tempo. La valutazione ripetuta di alcune query può comportare una notevole riduzione delle prestazioni.

- La valutazione di una query può avere come effetto collaterale la modifica del valore dei dati o dello stato del programma. Non tutte le query hanno effetti collaterali. Per determinare la possibilità di valutare una query in modo sicuro, senza effetti collaterali, è necessario conoscere il codice con cui la query viene implementata.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a>Esecuzione di istruzioni e LINQ
 Quando si esegue il debug di codice LINQ, l'esecuzione di istruzioni presenta alcune differenze di comportamento da tenere in considerazione.

### <a name="linq-to-sql"></a>LINQ to SQL
 Nelle query LINQ to SQL il codice del predicato non è sotto il controllo del debugger e pertanto non è possibile eseguirne le istruzioni. Qualsiasi query compilata in unalbero delle espressioni produce codice che non è sotto il controllo del debugger.

### <a name="stepping-in-visual-basic"></a>Esecuzione di istruzioni in Visual Basic
 Se, durante l'esecuzione di istruzioni tramite un programma Visual Basic, il debugger rileva una dichiarazione della query, non esegue le istruzioni della dichiarazione ma evidenzia l'intera dichiarazione come un'unica istruzione. Tale comportamento si verifica perché la query non viene valutata fino al momento della chiamata. Per altre informazioni, vedere [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 Se si eseguono le istruzioni contenute nell'esempio di codice seguente, il debugger evidenzia la dichiarazione della query o la creazione della query come un'unica istruzione.

```vb
Function MyFunction(ByVal x As Char)
    Return True
End Function

Sub Main()
    'Query creation
    Dim x = From it In "faoaoeua" _
            Where MyFunction(it) _
            Select New With {.a = it}

    ' Query execution
    For Each cur In x
        Console.WriteLine(cur.ToString())
    Next
End Sub
```

 Quando si esegue nuovamente l'istruzione, il debugger evidenzia `For Each cur In x`. Nel passaggio successivo viene eseguita la funzione `MyFunction`. Dopo aver eseguito le istruzioni di `MyFunction`, il debugger passa di nuovo a `Console.WriteLine(cur.ToSting())`. Le istruzioni del codice del predicato della dichiarazione della query non vengono mai eseguite, anche se il codice viene valutato dal debugger.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Sostituzione di un predicato con una funzione per attivare l'esecuzione di istruzioni (Visual Basic)
 Se è necessario eseguire le istruzioni del codice del predicato a fini di debug, è possibile sostituire il predicato con una chiamata a una funzione contenente il codice del predicato originale. Si supponga, ad esempio, di avere a disposizione il codice seguente:

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 È possibile spostare il codice del predicato in una funzione nuova, denominata `IsEven`:

```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt

For each item in query
      Console.WriteLine(item)
Next
...
Function IsEven(item As =Integer) as Boolean
      Return item Mod 2 = 0
End Function
```

 La query modificata chiama la funzione `IsEven` a ogni passaggio attraverso l'oggetto `items`. È possibile usare le finestre del debugger per verificare che ogni elemento soddisfi la condizione specificata ed eseguire il codice in `IsEven`. Il predicato contenuto nell'esempio seguente è abbastanza semplice. In presenza di un predicato più complesso di cui sia necessario eseguire il debug, tuttavia, questa tecnica può rivelarsi molto utile.

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a>Le operazioni di modifica e continuazione non sono supportate per LINQ
 Modifica e continuazione supporta modifiche alle query LINQ con limitazioni. Per informazioni dettagliate, vedere [Modifiche supportate da EnC](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)

## <a name="see-also"></a>Vedi anche

- [Debug di SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)
- [Introduzione alle query LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
