---
title: "CA2000: Eliminare gli oggetti prima che siano esterni all'ambito"
ms.date: 05/14/2019
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804982"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Eliminare gli oggetti prima che siano esterni all'ambito

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un oggetto locale di un <xref:System.IDisposable> tipo viene creato, ma l'oggetto non viene eliminato prima di tutti i riferimenti all'oggetto siano esterni all'ambito.

## <a name="rule-description"></a>Descrizione della regola

Se un oggetto eliminabile non viene eliminato in modo esplicito prima che tutti i relativi riferimenti siano esterni all'ambito, l'oggetto verrà eliminato in un momento indeterminato quando il garbage collector viene eseguito il finalizzatore dell'oggetto. Poiché potrebbe verificarsi un evento eccezionale che impedisca il finalizzatore dell'oggetto di esecuzione, l'oggetto deve essere eliminato in modo esplicito invece.

### <a name="special-cases"></a>Casi speciali

Anche se non viene eliminato l'oggetto, la regola CA2000 non viene generato per gli oggetti locali dei tipi seguenti:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Passaggio di un oggetto di uno di questi tipi per un costruttore e quindi assegnarlo a un campo indica un *dispose trasferimento della proprietà* per il tipo costruito. Vale a dire, il tipo costruito ora è responsabile dell'eliminazione dell'oggetto. Se il codice passa un oggetto di uno di questi tipi per un costruttore, non violazione della regola CA2000 si verifica anche se l'oggetto non viene eliminato prima di tutti i relativi riferimenti siano esterni all'ambito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, chiamare <xref:System.IDisposable.Dispose%2A> nell'oggetto prima che tutti i relativi riferimenti siano esterni all'ambito.

È possibile usare la [ `using` istruzione](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) in Visual Basic) per eseguire il wrapping di oggetti che implementano <xref:System.IDisposable>. Gli oggetti che vengono eseguito il wrapping in questo modo vengono eliminati automaticamente alla fine del `using` blocco. Tuttavia, nelle situazioni seguenti non deve o non può essere gestite con un `using` istruzione:

- Per restituire un oggetto eliminabile, deve costruito l'oggetto un `try/finally` bloccare all'esterno di un `using` blocco.

- Non si inizializza i membri di un oggetto disposable nel costruttore di una `using` istruzione.

- Quando i costruttori che sono protetti da un solo gestore di eccezioni sono annidati nel [parte di acquisizione di un `using` istruzione](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), un errore nel costruttore esterno può comportare l'oggetto creato dal costruttore nidificato mai in fase di chiusura. Nell'esempio seguente, un errore dei <xref:System.IO.StreamReader> costruttore può comportare il <xref:System.IO.FileStream> mai in fase di chiusura dell'oggetto. CA2000 flag in questo caso una violazione della regola.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Oggetti dinamici devono usare un oggetto shadow per implementare il modello dispose di <xref:System.IDisposable> oggetti.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non eliminare un avviso da questa regola, a meno che:

- È stato chiamato un metodo sull'oggetto che chiama `Dispose`, ad esempio <xref:System.IO.Stream.Close%2A>
- Il metodo che ha generato l'avviso restituisce un <xref:System.IDisposable> oggetto che esegue il wrapping dell'oggetto
- Il metodo di allocazione non dispone della proprietà dispose; vale a dire, la responsabilità di eliminare l'oggetto viene trasferita a un altro oggetto o un wrapper che ha creato nel metodo e restituito al chiamante

## <a name="related-rules"></a>Regole correlate

- [CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Esempio

Se si implementa un metodo che restituisce un oggetto disposable, usare un blocco try/finally senza un blocco catch per assicurarsi che l'oggetto viene eliminato. Usando un blocco try/finally, è consentire eccezioni a essere generata in corrispondenza del punto di errore e assicurarsi che l'oggetto viene eliminato.

Nel metodo OpenPort1, la chiamata per aprire l'oggetto SerialPort ISerializable o la chiamata a SomeMethod può avere esito negativo. Viene generato un avviso di CA2000 su questa implementazione.

Nel metodo OpenPort2, due oggetti SerialPort sono dichiarate e impostare questa proprietà su null:

- `tempPort`, che viene usato per verificare che le operazioni di metodo hanno esito positivo.

- `port`, che viene usato per il valore restituito del metodo.

Il `tempPort` viene costruito e aperto in un `try` necessari blocchi e qualsiasi altro lavoro viene eseguito nello stesso `try` blocco. Alla fine del `try` blocco, la porta aperta viene assegnato al `port` oggetti che verranno restituiti e la `tempPort` è impostata su `null`.

Il `finally` blocco controlla il valore di `tempPort`. Se non è null, non è riuscita un'operazione nel metodo, e `tempPort` sia chiuso per assicurarsi che tutte le risorse vengano rilasciate. Se le operazioni del metodo ha esito positivo oppure sarà null se non è riuscita un'operazione, l'oggetto porta restituita conterrà l'oggetto SerialPort aperto.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If

   End Try

   Return port

End Function
```

## <a name="example"></a>Esempio

Per impostazione predefinita, il compilatore Visual Basic ha tutti gli operatori aritmetici di controllo dell'overflow. Pertanto, qualsiasi operazione aritmetica di Visual Basic generi un <xref:System.OverflowException>. Questo potrebbe causare violazioni impreviste nelle regole, ad esempio CA2000. Ad esempio, la funzione seguente CreateReader1 produrrà una violazione di CA2000 perché il compilatore Visual Basic sta generando un'istruzione per l'aggiunta che potrebbe generare un'eccezione che impedirebbe la StreamReader non in fase di eliminazione di controllo dell'overflow.

Per risolvere questo problema, è possibile disabilitare l'emissione dei controlli dell'overflow dal compilatore Visual Basic nel progetto oppure è possibile modificare il codice della funzione CreateReader2 seguenti.

Per disabilitare l'emissione dei controlli dell'overflow, fare clic sul nome del progetto in Esplora soluzioni e quindi fare clic su **proprietà**. Fare clic su **Compile**, fare clic su **opzioni di compilazione avanzate**, quindi selezionare **Rimuovi controllo dell'overflow integer**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable>
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)