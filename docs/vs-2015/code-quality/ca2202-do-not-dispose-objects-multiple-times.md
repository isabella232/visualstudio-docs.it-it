---
title: 'CA2202: non eliminare oggetti più volte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667396"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Non eliminare oggetti più volte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un'implementazione di metodo contiene percorsi del codice che possono causare più chiamate a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o a un equivalente Dispose, ad esempio un metodo Close () su alcuni tipi, sullo stesso oggetto.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo di <xref:System.IDisposable.Dispose%2A> implementato correttamente può essere chiamato più volte senza generare un'eccezione. Tuttavia, ciò non è garantito e per evitare la generazione di un <xref:System.ObjectDisposedException?displayProperty=fullName> non è consigliabile chiamare <xref:System.IDisposable.Dispose%2A> più di una volta in un oggetto.

## <a name="related-rules"></a>Regole correlate
 [CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'implementazione in modo che, indipendentemente dal percorso del codice, <xref:System.IDisposable.Dispose%2A> venga chiamato una sola volta per l'oggetto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se <xref:System.IDisposable.Dispose%2A> per l'oggetto è noto come chiamabile in modo sicuro più volte, l'implementazione potrebbe cambiare in futuro.

## <a name="example"></a>Esempio
 Le istruzioni `using` annidate (`Using` in Visual Basic) possono causare violazioni dell'avviso CA2202. Se la risorsa IDisposable dell'istruzione `using` interna nidificata contiene la risorsa dell'istruzione `using` esterna, il metodo `Dispose` della risorsa nidificata rilascia la risorsa contenuta. Quando si verifica questa situazione, il metodo `Dispose` dell'istruzione `using` esterna tenta di eliminare la risorsa per la seconda volta.

 Nell'esempio seguente, un oggetto <xref:System.IO.Stream> creato in un'istruzione using esterna viene rilasciato alla fine dell'istruzione using interna nel metodo Dispose dell'oggetto <xref:System.IO.StreamWriter> che contiene l'oggetto `stream`. Alla fine dell'istruzione `using` esterna, l'oggetto `stream` viene rilasciato una seconda volta. La seconda versione è una violazione di CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Esempio
 Per risolvere questo problema, utilizzare un `try` / blocco `finally` anziché l'istruzione `using` esterna. Nel blocco `finally` assicurarsi che la risorsa `stream` non sia null.

```
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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Vedere anche
 [modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb) <xref:System.IDisposable?displayProperty=fullName>
