---
title: "CA2000: Eliminare gli oggetti prima di perdere l'ambito | Microsoft Docs"
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3456ec773b233da3ef2be1dfa7731460bdf6b44
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964052"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Eliminare gli oggetti prima che siano esterni all'ambito
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Category|Microsoft.Reliability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un oggetto locale di un <xref:System.IDisposable> tipo viene creato ma non viene eliminato l'oggetto prima che tutti i riferimenti all'oggetto siano esterni all'ambito.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Se un oggetto eliminabile non viene eliminato in modo esplicito prima che tutti i relativi riferimenti siano esterni all'ambito, l'oggetto verrà eliminato in un momento indeterminato quando il garbage collector viene eseguito il finalizzatore dell'oggetto. Poiché potrebbe verificarsi un evento eccezionale che impedisca il finalizzatore dell'oggetto di esecuzione, l'oggetto deve essere eliminato in modo esplicito invece.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> nell'oggetto prima che tutti i relativi riferimenti siano esterni all'ambito.  
  
 Si noti che è possibile usare la `using` istruzione (`Using` nelle [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) per eseguire il wrapping di oggetti che implementano `IDisposable`. Gli oggetti che vengono eseguito il wrapping in questo modo verranno automaticamente eliminati alla chiusura del `using` blocco.  
  
 Di seguito sono alcune situazioni in cui l'istruzione using non è sufficiente per proteggere gli oggetti IDisposable e può causare CA2000 si verifichi.  
  
-   Restituzione di un oggetto disposable richiede che l'oggetto viene costruito in un blocco try/finally all'esterno una tramite blocco.  
  
-   L'inizializzazione dei membri di un oggetto disposable non deve essere eseguita nel costruttore dell'uso di un'istruzione.  
  
-   Costruttori protetti solo da un gestore di eccezioni di annidamento. Ad esempio,  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     fa sì che CA2000 perché un errore nella costruzione dell'oggetto StreamReader può comportare l'oggetto FileStream mai in fase di chiusura.  
  
-   Oggetti dinamici devono usare un oggetto di ombreggiatura per implementare il modello Dispose di oggetti IDisposable.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non eliminare un avviso da questa regola a meno che non sia stato chiamato un metodo sull'oggetto che chiama `Dispose`, come <xref:System.IO.Stream.Close%2A>, o se il metodo che ha generato l'avviso restituisce un oggetto IDisposable che fa il wrapping dell'oggetto.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>Esempio  
 Se si implementa un metodo che restituisce un oggetto disposable, usare un blocco try/finally senza un blocco catch per assicurarsi che l'oggetto viene eliminato. Usando un blocco try/finally, è consentire eccezioni a essere generata in corrispondenza del punto di errore e assicurarsi che l'oggetto viene eliminato.  
  
 Nel metodo OpenPort1, la chiamata per aprire l'oggetto SerialPort ISerializable o la chiamata a SomeMethod può avere esito negativo. Viene generato un avviso di CA2000 su questa implementazione.  
  
 Nel metodo OpenPort2, due oggetti SerialPort sono dichiarate e impostare questa proprietà su null:  
  
- `tempPort`, che viene usato per verificare che le operazioni di metodo hanno esito positivo.  
  
- `port`, che viene usato per il valore restituito del metodo.  
  
  Il `tempPort` viene costruito e aperto in un `try` necessari blocchi e qualsiasi altro lavoro viene eseguito nello stesso `try` blocco. Alla fine del `try` blocco, la porta aperta viene assegnato al `port` oggetti che verranno restituiti e la `tempPort` è impostata su `null`.  
  
  Il `finally` blocco controlla il valore di `tempPort`. Se non è null, non è riuscita un'operazione nel metodo, e `tempPort` sia chiuso per assicurarsi che tutte le risorse vengano rilasciate. Se le operazioni del metodo ha esito positivo oppure sarà null se non è riuscita un'operazione, l'oggetto porta restituita conterrà l'oggetto SerialPort aperto.  
  
  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]  
  
## <a name="example"></a>Esempio  
 Per impostazione predefinita, il [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilatore dispone di operatori aritmetici verificare la presenza di overflow. Pertanto, qualsiasi operazione aritmetica di Visual Basic generi un <xref:System.OverflowException>. Questo potrebbe causare violazioni impreviste nelle regole, ad esempio CA2000. Ad esempio, la funzione seguente CreateReader1 produrrà una violazione di CA2000 perché il compilatore Visual Basic sta generando un'istruzione per l'aggiunta che potrebbe generare un'eccezione che impedirebbe la StreamReader non in fase di eliminazione di controllo dell'overflow.  
  
 Per risolvere questo problema, è possibile disabilitare l'emissione dei controlli dell'overflow dal compilatore Visual Basic nel progetto oppure è possibile modificare il codice della funzione CreateReader2 seguenti.  
  
 Per disabilitare l'emissione dei controlli dell'overflow, fare clic sul nome del progetto in Esplora soluzioni e quindi fare clic su **proprietà**. Fare clic su **Compile**, fare clic su **opzioni di compilazione avanzate**, quindi selezionare **Rimuovi controllo dell'overflow integer**.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IDisposable>   
 [Criterio Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)