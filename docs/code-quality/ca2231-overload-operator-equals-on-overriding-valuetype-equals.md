---
title: "CA2231: Eseguire l'overload dell'operatore \"uguale a\" all'override di ValueType.Equals"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b5826633737c3bb7d8f358ff090f0b1a55ac8eef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231052"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo di valore <xref:System.Object.Equals%2A?displayProperty=fullName> esegue l'override di, ma non implementa l'operatore di uguaglianza.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Nella maggior parte dei linguaggi di programmazione non esiste alcuna implementazione predefinita dell'operatore di uguaglianza (= =) per i tipi di valore. Se il linguaggio di programmazione supporta gli overload degli operatori, è consigliabile implementare l'operatore di uguaglianza. Il comportamento deve essere identico a quello <xref:System.Object.Equals%2A>di.

Non è possibile usare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza. Questa operazione provocherà un overflow dello stack. Per implementare l'operatore di uguaglianza, usare il metodo Object. Equals nell'implementazione. Ad esempio:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola in modo sicuro; Tuttavia, se possibile, è consigliabile fornire l'operatore di uguaglianza.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca2231.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (utilizzo). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene definito un tipo che viola la regola:

[!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1046: Non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Gli overload degli operatori hanno alternative denominate](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2226: Gli operatori devono avere Overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Esegue l'override di Equals in un operatore di overload uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Eseguire l'override di GetHashCode sull'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Object.Equals%2A?displayProperty=fullName>