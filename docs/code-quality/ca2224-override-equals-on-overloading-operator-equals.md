---
title: "CA2224: Eseguire l'override di Equals all'overload dell'operatore \"uguale a\""
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231212"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eseguire l'override di Equals all'overload dell'operatore "uguale a"

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue <xref:System.Object.Equals%2A?displayProperty=fullName>l'override di.

## <a name="rule-description"></a>Descrizione della regola

L'operatore di uguaglianza è concepito come un modo sintatticamente pratico per accedere alla funzionalità <xref:System.Object.Equals%2A> del metodo. Se si implementa l'operatore di uguaglianza, la relativa logica deve essere identica a <xref:System.Object.Equals%2A>quella di.

Il C# compilatore genera un avviso se il codice viola questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, è necessario rimuovere l'implementazione dell'operatore di uguaglianza oppure eseguire l'override <xref:System.Object.Equals%2A> di e fare in modo che i due metodi restituiscano gli stessi valori. Se l'operatore di uguaglianza non introduce un comportamento incoerente, è possibile correggere la violazione fornendo un'implementazione di <xref:System.Object.Equals%2A> che chiama il <xref:System.Object.Equals%2A> metodo nella classe di base.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola se l'operatore di uguaglianza restituisce lo stesso valore dell'implementazione ereditata di <xref:System.Object.Equals%2A>. Gli esempi in questo articolo includono un tipo che potrebbe eliminare in modo sicuro un avviso da questa regola.

## <a name="examples-of-inconsistent-equality-definitions"></a>Esempi di definizioni di uguaglianza incoerenti

Nell'esempio seguente viene illustrato un tipo con definizioni incoerenti di uguaglianza. `BadPoint`modifica il significato di uguaglianza fornendo un'implementazione personalizzata dell'operatore di uguaglianza, ma non esegue l'override <xref:System.Object.Equals%2A> di in modo che si comportano in modo identico.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Il codice seguente verifica il comportamento di `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Questo esempio produce il seguente output:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

Nell'esempio seguente viene illustrato un tipo che tecnicamente viola questa regola, ma che non si comporta in modo incoerente.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Il codice seguente verifica il comportamento di `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Questo esempio produce il seguente output:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Esempio di classe

Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che viola questa regola.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Nell'esempio seguente viene corretta la violazione eseguendo l' <xref:System.Object.Equals%2A?displayProperty=fullName>override di.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Esempio di struttura

Nell'esempio seguente viene illustrata una struttura (tipo di valore) che viola la regola:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Nell'esempio seguente viene corretta la violazione eseguendo l' <xref:System.ValueType.Equals%2A?displayProperty=fullName>override di.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Regole correlate

[CA1046: Non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Gli overload degli operatori hanno alternative denominate](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Gli operatori devono avere Overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Eseguire l'override di GetHashCode sull'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)