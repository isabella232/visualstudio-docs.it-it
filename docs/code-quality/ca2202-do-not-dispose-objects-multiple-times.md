---
title: 'CA2202: Non eliminare oggetti più volte'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e805cb76ebe4c216b456f65ea3264f8f25561cc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548608"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Non eliminare oggetti più volte

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un'implementazione del metodo contiene percorsi di codice che potrebbero comportare più chiamate a <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> o un equivalente di Dispose, ad esempio un metodo Close () su alcuni tipi, sullo stesso oggetto.

## <a name="rule-description"></a>Descrizione della regola

Oggetto implementato correttamente <xref:System.IDisposable.Dispose%2A> metodo può essere chiamato più volte senza generare un'eccezione. Tuttavia, non è garantita e per evitare di generare una <xref:System.ObjectDisposedException?displayProperty=fullName> non è necessario chiamare <xref:System.IDisposable.Dispose%2A> più di una volta su un oggetto.

## <a name="related-rules"></a>Regole correlate

- [CA2000: Eliminare gli oggetti prima di perdere l'ambito](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare quindi vale indipendentemente dal fatto che l'implementazione del percorso di codice, <xref:System.IDisposable.Dispose%2A> viene chiamato solo una volta per l'oggetto.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola. Anche se <xref:System.IDisposable.Dispose%2A> per l'oggetto è noto per essere chiamato in modo sicuro più volte, l'implementazione potrà cambiare in futuro.

## <a name="example"></a>Esempio

Annidato `using` istruzioni (`Using` in Visual Basic) possono provocare violazioni dell'avviso CA2202. Se la risorsa di IDisposable di interna annidata `using` istruzione contiene la risorsa di esterna `using` istruzione, il `Dispose` metodo della risorsa annidata rilascia la risorsa contenuta. Quando si verifica questa situazione, il `Dispose` metodo di esterna `using` istruzione tenta di eliminare la propria risorsa per la seconda volta.

Nell'esempio seguente, un <xref:System.IO.Stream> oggetto che viene creato in un outer utilizzando l'istruzione viene rilasciato alla fine della parte interna usando l'istruzione nel metodo Dispose della <xref:System.IO.StreamWriter> oggetto che contiene il `stream` oggetto. Alla fine di esterna `using` istruzione, il `stream` oggetto viene rilasciato una seconda volta. Il secondo rilascio costituisce una violazione del CA2202.

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

Per risolvere questo problema, usare una `try` / `finally` blocco anziché esterna `using` istruzione. Nel `finally` blocco, assicurarsi che il `stream` risorsa non è null.

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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Vedere anche

- <xref:System.IDisposable?displayProperty=fullName>
- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)