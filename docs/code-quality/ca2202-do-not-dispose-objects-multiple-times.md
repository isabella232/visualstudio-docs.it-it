---
title: 'CA2202: Non eliminare gli oggetti più volte'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7fa7756383426f990e18225995a768de9fefbd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231729"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Non eliminare gli oggetti più volte

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un'implementazione di metodo contiene percorsi del codice che possono causare più <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chiamate a o a un equivalente Dispose, ad esempio un metodo Close () su alcuni tipi, sullo stesso oggetto.

## <a name="rule-description"></a>Descrizione della regola

Un metodo implementato <xref:System.IDisposable.Dispose%2A> correttamente può essere chiamato più volte senza generare un'eccezione. Tuttavia, ciò non è garantito e per evitare la generazione <xref:System.ObjectDisposedException?displayProperty=fullName> di un non è <xref:System.IDisposable.Dispose%2A> consigliabile chiamare più di una volta in un oggetto.

## <a name="related-rules"></a>Regole correlate

- [CA2000 Elimina gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare l'implementazione in modo che, indipendentemente dal percorso del <xref:System.IDisposable.Dispose%2A> codice, venga chiamata solo una volta per l'oggetto.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. Anche se <xref:System.IDisposable.Dispose%2A> per l'oggetto è noto che è possibile chiamare in modo sicuro più volte, l'implementazione potrebbe cambiare in futuro.

## <a name="example"></a>Esempio

Le `using` istruzioni nidificate (`Using` in Visual Basic) possono causare violazioni dell'avviso CA2202. Se la risorsa IDisposable dell'istruzione interna `using` nidificata contiene la risorsa dell'istruzione esterna `using` , il `Dispose` metodo della risorsa nidificata rilascia la risorsa contenuta. Quando si verifica questa situazione, `Dispose` il metodo dell'istruzione `using` esterna tenta di eliminare la risorsa per la seconda volta.

Nell'esempio seguente, un <xref:System.IO.Stream> oggetto creato in un'istruzione using esterna viene rilasciato alla fine dell'istruzione using interna nel metodo Dispose <xref:System.IO.StreamWriter> dell'oggetto che contiene l' `stream` oggetto. Alla fine dell'istruzione esterna `using` , l' `stream` oggetto viene rilasciato una seconda volta. La seconda versione è una violazione di CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Esempio

Per risolvere questo problema, usare un `try` / `finally` blocco anziché l'istruzione esterna `using` . Nel blocco verificare che la `stream` risorsa non sia null. `finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> La `?.` sintassi precedente è l' [operatore condizionale null](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-).

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable?displayProperty=fullName>
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)