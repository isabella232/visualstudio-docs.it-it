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
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546289"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Non eliminare gli oggetti più volte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un'implementazione di metodo contiene percorsi del codice che possono causare più chiamate a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o a un equivalente Dispose, ad esempio un metodo Close () su alcuni tipi, sullo stesso oggetto.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo implementato correttamente <xref:System.IDisposable.Dispose%2A> può essere chiamato più volte senza generare un'eccezione. Tuttavia, ciò non è garantito e per evitare la generazione di un non è <xref:System.ObjectDisposedException?displayProperty=fullName> consigliabile chiamare <xref:System.IDisposable.Dispose%2A> più di una volta in un oggetto.

## <a name="related-rules"></a>Regole correlate
 [CA2000: Eliminare gli oggetti prima che siano esterni all'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'implementazione in modo che, indipendentemente dal percorso del codice, <xref:System.IDisposable.Dispose%2A> venga chiamata solo una volta per l'oggetto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se <xref:System.IDisposable.Dispose%2A> per l'oggetto è noto che è possibile chiamare in modo sicuro più volte, l'implementazione potrebbe cambiare in futuro.

## <a name="example"></a>Esempio
 `using`Le istruzioni nidificate ( `Using` in Visual Basic) possono causare violazioni dell'avviso CA2202. Se la risorsa IDisposable dell'istruzione interna nidificata `using` contiene la risorsa dell'istruzione esterna `using` , il `Dispose` metodo della risorsa nidificata rilascia la risorsa contenuta. Quando si verifica questa situazione, il `Dispose` metodo dell' `using` istruzione esterna tenta di eliminare la risorsa per la seconda volta.

 Nell'esempio seguente, un <xref:System.IO.Stream> oggetto creato in un'istruzione using esterna viene rilasciato alla fine dell'istruzione using interna nel metodo Dispose dell' <xref:System.IO.StreamWriter> oggetto che contiene l' `stream` oggetto. Alla fine dell' `using` istruzione esterna, l' `stream` oggetto viene rilasciato una seconda volta. La seconda versione è una violazione di CA2202.

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
 Per risolvere questo problema, usare un `try` / `finally` blocco anziché l'istruzione esterna `using` . Nel `finally` blocco verificare che la `stream` risorsa non sia null.

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
 <xref:System.IDisposable?displayProperty=fullName> [Modello Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
