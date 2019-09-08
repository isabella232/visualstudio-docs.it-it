---
title: 'CA1002: Non esporre elenchi generici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 621bb7292ca467d6d3197636f662a4662712d483
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766016"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Non esporre elenchi generici

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo contiene un membro visibile esternamente che è un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo, restituisce un <xref:System.Collections.Generic.List%601> tipo o la cui firma include un <xref:System.Collections.Generic.List%601> parametro.

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Collections.Generic.List%601?displayProperty=fullName>è una raccolta generica progettata per le prestazioni e non per l'ereditarietà. <xref:System.Collections.Generic.List%601>non contiene membri virtuali che semplificano la modifica del comportamento di una classe ereditata. Le raccolte generiche seguenti sono progettate per l'ereditarietà e devono essere esposte anziché <xref:System.Collections.Generic.List%601>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo in una delle raccolte generiche progettate per l'ereditarietà.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare un avviso da questa regola a meno che l'assembly che genera questo avviso non sia destinato a essere una libreria riutilizzabile. È ad esempio possibile che l'avviso non venga eliminato in un'applicazione ottimizzata per le prestazioni, in cui è stato ottenuto un vantaggio in merito alle prestazioni dall'utilizzo di elenchi generici.

## <a name="related-rules"></a>Regole correlate

[CA1005 Evitare parametri eccessivi nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006 Non annidare tipi generici nelle firme membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 I metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usare i generics laddove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

[Generics](/dotnet/csharp/programming-guide/generics/index)
