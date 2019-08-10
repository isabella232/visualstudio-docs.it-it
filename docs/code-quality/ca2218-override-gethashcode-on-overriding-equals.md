---
title: "CA2218: Eseguire l'override di GetHashCode all'override di Equals"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dbd8580f5aaeb88c08d35b50258510cb1a85ba2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920297"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Eseguire l'override di GetHashCode all'override di Equals

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
Un tipo pubblico esegue <xref:System.Object.Equals%2A?displayProperty=fullName> l'override, ma <xref:System.Object.GetHashCode%2A?displayProperty=fullName>non esegue l'override.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Object.GetHashCode%2A>Restituisce un valore, in base all'istanza corrente, adatto per algoritmi di hash e strutture di dati, ad esempio una tabella hash. Due oggetti dello stesso tipo e sono uguali devono restituire lo stesso codice hash per assicurarsi che le istanze dei seguenti tipi funzionino correttamente:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Tipi che implementano<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.GetHashCode%2A>. Per una coppia di oggetti dello stesso tipo, è necessario assicurarsi che l'implementazione restituisca lo stesso valore se l'implementazione di <xref:System.Object.Equals%2A> restituisce `true` per la coppia.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="class-example"></a>Esempio di classe

### <a name="description"></a>Descrizione
Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che viola questa regola.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Commenti
Nell'esempio seguente viene corretta la violazione eseguendo l' <xref:System.Object.GetHashCode>override di.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Esempio di struttura

### <a name="description"></a>Descrizione
Nell'esempio seguente viene illustrata una struttura (tipo di valore) che viola questa regola.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Commenti
Nell'esempio seguente viene corretta la violazione eseguendo l' <xref:System.Object.GetHashCode>override di.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1046: Non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Gli overload degli operatori hanno alternative denominate](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Gli operatori devono avere Overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224: Esegue l'override di Equals in un operatore di overload uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)