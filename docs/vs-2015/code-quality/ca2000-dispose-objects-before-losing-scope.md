---
title: "CA2000: eliminare gli oggetti prima di perdere l'ambito | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89e0797afdcf299bb466018049a6d1217c5ad2dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666164"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Eliminare gli oggetti prima di perdere l'ambito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Category|Microsoft. affidabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Viene creato un oggetto locale di un tipo di <xref:System.IDisposable>, ma l'oggetto non viene eliminato prima che tutti i riferimenti all'oggetto siano fuori dall'ambito.

## <a name="rule-description"></a>Descrizione della regola
 Se un oggetto Disposable non viene eliminato in modo esplicito prima che tutti i relativi riferimenti siano fuori dall'ambito, l'oggetto verrà eliminato in un momento indeterminato quando il Garbage Collector esegue il finalizzatore dell'oggetto. Poiché è possibile che si verifichi un evento eccezionale che impedisce l'esecuzione del finalizzatore dell'oggetto, l'oggetto deve essere eliminato in modo esplicito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> sull'oggetto prima che tutti i relativi riferimenti siano fuori dall'ambito.

 Si noti che è possibile usare l'istruzione `using` (`Using` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) per eseguire il wrapping degli oggetti che implementano `IDisposable`. Gli oggetti di cui viene eseguito il wrapper in questo modo verranno eliminati automaticamente alla chiusura del blocco `using`.

 Di seguito sono riportate alcune situazioni in cui l'istruzione using non è sufficiente per proteggere gli oggetti IDisposable e può causare il verificarsi di CA2000.

- Per restituire un oggetto Disposable è necessario che l'oggetto venga costruito in un blocco try/finally all'esterno di un blocco using.

- L'inizializzazione dei membri di un oggetto Disposable non deve essere eseguita nel costruttore di un'istruzione using.

- Costruttori di annidamento protetti solo da un gestore di eccezioni. Di seguito è riportato un esempio:

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     causa il verificarsi di CA2000 perché un errore nella costruzione dell'oggetto StreamReader può comportare la chiusura dell'oggetto FileStream.

- Gli oggetti dinamici devono usare un oggetto Shadow per implementare il modello Dispose degli oggetti IDisposable.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola a meno che non sia stato chiamato un metodo sull'oggetto che chiama `Dispose`, come <xref:System.IO.Stream.Close%2A>, o se il metodo che ha generato l'avviso restituisce un oggetto IDisposable che fa il wrapping dell'oggetto.

## <a name="related-rules"></a>Regole correlate
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Esempio
 Se si implementa un metodo che restituisce un oggetto eliminabile, utilizzare un blocco try/finally senza un blocco catch per assicurarsi che l'oggetto venga eliminato. Utilizzando un blocco try/finally, si consente la generazione di eccezioni in corrispondenza del punto di errore e assicurarsi che l'oggetto venga eliminato.

 Nel metodo OpenPort1 la chiamata per aprire l'oggetto ISerializable SerialPort o la chiamata a SomeMethod può avere esito negativo. In questa implementazione viene generato un avviso CA2000.

 Nel metodo OpenPort2 due oggetti SerialPort sono dichiarati e impostati su null:

- `tempPort`, utilizzato per verificare l'esito positivo delle operazioni del metodo.

- `port`, che viene usato per il valore restituito del metodo.

  Il `tempPort` viene costruito e aperto in un blocco `try` e qualsiasi altra operazione richiesta viene eseguita nello stesso blocco `try`. Alla fine del blocco `try`, la porta aperta viene assegnata all'oggetto `port` che verrà restituito e l'oggetto `tempPort` viene impostato su `null`.

  Il blocco `finally` controlla il valore di `tempPort`. Se non è null, un'operazione nel metodo ha esito negativo e `tempPort` viene chiusa per assicurarsi che tutte le risorse vengano rilasciate. L'oggetto della porta restituita conterrà l'oggetto SerialPort aperto se le operazioni del metodo hanno avuto esito positivo o se un'operazione non è riuscita.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>Esempio
 Per impostazione predefinita, il compilatore [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dispone di tutti gli operatori aritmetici che controllano l'overflow. Pertanto, qualsiasi operazione aritmetica Visual Basic potrebbe generare una <xref:System.OverflowException>. Questo potrebbe causare violazioni impreviste in regole come CA2000. La funzione CreateReader1 seguente, ad esempio, genererà una violazione CA2000 perché il compilatore Visual Basic emette un'istruzione di controllo dell'overflow per l'aggiunta che potrebbe generare un'eccezione che provocherebbe la mancata eliminazione di StreamReader.

 Per risolvere questo problema, è possibile disabilitare la creazione di controlli di overflow da parte del compilatore Visual Basic nel progetto oppure modificare il codice come nella funzione CreateReader2 seguente.

 Per disabilitare la creazione dei controlli di overflow, fare clic con il pulsante destro del mouse sul nome del progetto in Esplora soluzioni e quindi scegliere **Proprietà**. Fare clic su **Compila**, fare clic su **Opzioni di compilazione avanzate**, quindi selezionare **Rimuovi controlli di overflow di Integer**.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>Vedere anche
 [modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable>