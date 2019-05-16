---
title: Debug di LINQ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0292bf5b62bf150a598b4c750929ba6928216a50
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691266"
---
# <a name="debugging-linq"></a>Debug di LINQ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] supporta il debug di codice LINQ (Language Integrated Query), con alcune limitazioni. La maggior parte delle funzionalità di debug è compatibile con le istruzioni LINQ, inclusa l'esecuzione di istruzioni, l'impostazione di punti di interruzione e la visualizzazione dei risultati nelle finestre del debugger. In questo argomento vengono descritte le principali limitazioni del debug di codice LINQ.  
  
## <a name="BKMK_ViewingLINQResults"></a>Visualizzazione dei risultati LINQ  
 È possibile visualizzare il risultato di un'istruzione LINQ usando i suggerimenti dati, la finestra Espressioni di controllo e la finestra di dialogo Controllo immediato. Quando si usa una finestra di origine, passare con il puntatore su una query nella finestra di origine per visualizzare un suggerimento dati. È possibile copiare una variabile LINQ e incollarla nella finestra Espressioni di controllo o nella finestra di dialogo Controllo immediato.  
  
 In LINQ, le query non vengono valutate al momento della creazione o della dichiarazione, ma soltanto al momento dell'uso. La query non dispone pertanto di un valore fino a quando non viene valutata. Per una descrizione completa della creazione di query e la valutazione, vedere [Introduzione alle query LINQ (c#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) oppure [Writing Your prima Query LINQ](https://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Per visualizzare il risultato di una query, è necessario che venga valutata dal debugger. Tenere presenti alcuni effetti della valutazione implicita, che avviene quando si visualizza il risultato di una query LINQ nel debugger:  
  
- La singola valutazione della query e l'espansione del nodo dei risultati richiedono tempo. La valutazione ripetuta di alcune query può comportare una notevole riduzione delle prestazioni.  
  
- La valutazione di una query può avere come effetto collaterale la modifica del valore dei dati o dello stato del programma. Non tutte le query hanno effetti collaterali. Per determinare la possibilità di valutare una query in modo sicuro, senza effetti collaterali, è necessario conoscere il codice con cui la query viene implementata.  
  
## <a name="BKMK_SteppingAndLinq"></a>Esecuzione di istruzioni e LINQ  
 Quando si esegue il debug di codice LINQ, l'esecuzione di istruzioni presenta alcune differenze di comportamento da tenere in considerazione.  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 Nelle query LINQ to SQL il codice del predicato non è sotto il controllo del debugger e pertanto non è possibile eseguirne le istruzioni. Qualsiasi query compilata in unalbero delle espressioni produce codice che non è sotto il controllo del debugger.  
  
### <a name="stepping-in-visual-basic"></a>Esecuzione di istruzioni in Visual Basic  
 Se, durante l'esecuzione di istruzioni tramite un programma Visual Basic, il debugger rileva una dichiarazione della query, non esegue le istruzioni della dichiarazione ma evidenzia l'intera dichiarazione come un'unica istruzione. Tale comportamento si verifica perché la query non viene valutata fino al momento della chiamata. Per altre informazioni, vedere [Introduzione a LINQ in Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Se si eseguono le istruzioni contenute nell'esempio di codice seguente, il debugger evidenzia la dichiarazione della query o la creazione della query come un'unica istruzione.  
  
```  
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
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 È possibile spostare il codice del predicato in una funzione nuova, denominata `IsEven`:  
  
```  
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
  
## <a name="BKMK_EditandContinueNotSupportedforLINQ"></a>Le operazioni di modifica e continuazione non sono supportate per LINQ  
 In Modifica e continuazione non è supportata la modifica di query LINQ. Se si tenta di aggiungere, rimuovere o modificare un'istruzione LINQ durante una sessione di debug, viene visualizzata una finestra di dialogo indicante che tale modifica non è supportata da Modifica e continuazione. A questo punto è possibile annullare la modifica oppure interrompere la sessione di debug per avviare una nuova sessione con il codice modificato.  
  
 In Modifica e continuazione non è supportata neppure la modifica del tipo o del valore delle variabili usate in istruzioni LINQ. Anche in questo caso è possibile annullare le modifiche oppure interrompere e riavviare la sessione di debug.  
  
 In C#, non è possibile usare Modifica e continuazione su nessun tipo di codice in un metodo contenente una query LINQ.  
  
 In Visual Basic, è possibile usare Modifica e continuazione su codice non LINQ anche in metodi contenente una query LINQ. È possibile aggiungere o rimuovere codice prima dell'istruzione LINQ, anche se le modifiche influiscono sul numero di riga della query LINQ. Le modalità di esecuzione del debug Visual Basic di codice non LINQ rimangono invariate rispetto a prima dell'introduzione di LINQ. Non è tuttavia possibile modificare, aggiungere o rimuovere query LINQ, a meno che non si voglia interrompere il debug per applicare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug SQL](https://msdn.microsoft.com/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Side Effects and Expressions](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Gestione delle eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Introduzione alle query LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)   
 [Introduzione a LINQ in Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)
