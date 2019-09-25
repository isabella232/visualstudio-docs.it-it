---
title: 'CA1816: Chiamare GC.SuppressFinalize correttamente'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233534"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Chiamare GC.SuppressFinalize correttamente

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilizzo|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Le violazioni di questa regola possono essere causate da:

- Metodo che è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> e non chiama. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Metodo che non è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> e chiama. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Metodo che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> e passa un valore diverso da [this (C#)](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Descrizione della regola

Il <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodo consente agli utenti di rilasciare le risorse in qualsiasi momento prima che l'oggetto diventi disponibile per Garbage Collection. Se viene <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> chiamato il metodo, vengono liberate le risorse dell'oggetto. Questa operazione rende superflua la finalizzazione. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>deve chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> in modo che il Garbage Collector non chiami il finalizzatore dell'oggetto.

Per impedire che i tipi derivati con finalizzatori debbano reimplementare <xref:System.IDisposable> e chiamarlo, i tipi non sealed senza finalizzatori devono comunque chiamare. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola:

- Se il metodo è un'implementazione di <xref:System.IDisposable.Dispose%2A>, aggiungere una chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Se il metodo non è un'implementazione di <xref:System.IDisposable.Dispose%2A>, rimuovere la chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> o spostarla nell' <xref:System.IDisposable.Dispose%2A> implementazione del tipo.

- Modificare tutte le chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> a per passare [thisC#()](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola solo se si utilizza <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> intenzionalmente per controllare la durata di altri oggetti. Non eliminare un avviso da questa regola se un'implementazione di <xref:System.IDisposable.Dispose%2A> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. In questa situazione, la mancata eliminazione della finalizzazione comporta un peggioramento delle prestazioni e non offre alcun vantaggio.

## <a name="example-that-violates-ca1816"></a>Esempio che viola CA1816

Questo codice mostra un metodo che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, ma non passa [this (C#)](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Di conseguenza, questo codice viola la regola CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Esempio che soddisfa CA1816

Questo esempio mostra un metodo che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> correttamente passando [this (C#)](/dotnet/csharp/language-reference/keywords/this) o [me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2215: I metodi Dispose devono chiamare Dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216 I tipi Disposable devono dichiarare Finalizer](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vedere anche

- [Modello Dispose](/dotnet/standard/design-guidelines/dispose-pattern)