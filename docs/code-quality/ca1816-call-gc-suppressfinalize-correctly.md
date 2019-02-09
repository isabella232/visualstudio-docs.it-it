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
ms.openlocfilehash: 2c14f9ed8803c02d1570ac2a3dee82fbdfca5f01
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948537"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Chiamare GC.SuppressFinalize correttamente

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Category|Microsoft. Utilizzo|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Le violazioni di questa regola possono essere causate da:

- Un metodo che è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> e non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Un metodo che non è un'implementazione di <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> e chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Un metodo che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> e passa un elemento diverso da [questo (c#)](/dotnet/csharp/language-reference/keywords/this) oppure [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Descrizione della regola

Il <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodo consente agli utenti di rilasciare le risorse in qualsiasi momento prima dell'oggetto di essere disponibili per l'operazione di garbage collection. Se il <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> viene chiamato il metodo, libera le risorse dell'oggetto. In questo modo la finalizzazione non necessaria. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> deve chiamare <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> in modo che il garbage collector non chiama il finalizzatore dell'oggetto.

Per impedire i tipi derivati con i finalizzatori di dover implementare nuovamente <xref:System.IDisposable> e per la chiamata, i tipi unsealed senza i finalizzatori devono chiamare ancora <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola:

- Se il metodo è un'implementazione di <xref:System.IDisposable.Dispose%2A>, aggiungere una chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Se il metodo non è un'implementazione di <xref:System.IDisposable.Dispose%2A>, rimuovere la chiamata a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> o spostarlo nel tipo <xref:System.IDisposable.Dispose%2A> implementazione.

- Modificare tutte le chiamate a <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> per passare [questo (c#)](/dotnet/csharp/language-reference/keywords/this) oppure [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare solo un avviso da questa regola se si usa deliberatamente <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> per controllare la durata di altri oggetti. Non eliminare un avviso da questa regola se un'implementazione di <xref:System.IDisposable.Dispose%2A> non chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. In questo caso, riesce a eliminare la finalizzazione comporta una riduzione delle prestazioni e non offre alcun vantaggio.

## <a name="example-that-violates-ca1816"></a>Esempio che viola CA1816

Questo codice viene illustrato un metodo che chiama <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, ma non viene superato [questo (c#)](/dotnet/csharp/language-reference/keywords/this) oppure [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). Di conseguenza, questo codice viola la regola CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Esempio che soddisfa CA1816

In questo esempio viene illustrato un metodo che correttamente le chiamate <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> passando [questo (c#)](/dotnet/csharp/language-reference/keywords/this) oppure [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2215: I metodi Dispose devono chiamare dispose della classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: I tipi Disposable devono dichiarare un finalizzatore](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Vedere anche

- [Criterio Dispose](/dotnet/standard/design-guidelines/dispose-pattern)