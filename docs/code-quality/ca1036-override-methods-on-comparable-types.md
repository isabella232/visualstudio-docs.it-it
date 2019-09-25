---
title: "CA1036: Eseguire l'override di metodi su tipi confrontabili"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be340314afe36f3a930474f345715965f566b2d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236001"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Eseguire l'override di metodi su tipi confrontabili

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo implementa l' <xref:System.IComparable?displayProperty=fullName> interfaccia e non esegue l' <xref:System.Object.Equals%2A?displayProperty=fullName> override o non esegue l'overload dell'operatore specifico della lingua per uguaglianza, disuguaglianza, minore di o maggiore di. La regola non segnala una violazione se il tipo eredita solo un'implementazione dell'interfaccia.

Per impostazione predefinita, questa regola esamina solo i tipi pubblici e protetti, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

I tipi che definiscono un ordinamento personalizzato implementano <xref:System.IComparable> l'interfaccia. Il <xref:System.IComparable.CompareTo%2A> metodo restituisce un valore intero che indica l'ordinamento corretto per due istanze del tipo. Questa regola identifica i tipi che impostano un ordinamento. L'impostazione di un ordinamento implica la mancata applicazione del significato comune di uguaglianza, disuguaglianza, minore di e maggiore di. Quando si fornisce un'implementazione di <xref:System.IComparable>, è necessario in genere eseguire <xref:System.Object.Equals%2A> l'override di in modo che restituisca valori <xref:System.IComparable.CompareTo%2A>coerenti con. Se si esegue <xref:System.Object.Equals%2A> l'override di e si codifica in un linguaggio che supporta gli overload degli operatori, è necessario fornire anche operatori coerenti <xref:System.Object.Equals%2A>con.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, eseguire <xref:System.Object.Equals%2A>l'override di. Se il linguaggio di programmazione supporta l'overload degli operatori, fornire gli operatori seguenti:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

In C#i token utilizzati per rappresentare questi operatori sono i seguenti:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso dalla regola CA1036 quando la violazione è causata da operatori mancanti e il linguaggio di programmazione non supporta l'overload degli operatori, come avviene con Visual Basic. Se si determina che l'implementazione degli operatori non è sensata nel contesto dell'applicazione, è anche possibile eliminare un avviso da questa regola quando viene attivato su operatori di uguaglianza diversi da op_Equality. Tuttavia, se si esegue l'override <xref:System.Object.Equals%2A?displayProperty=nameWithType>di, è sempre necessario eseguire l'override di op_Equality e dell'operatore = =.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="examples"></a>Esempi

Il codice seguente contiene un tipo che implementa <xref:System.IComparable>correttamente. I commenti del codice identificano i metodi che soddisfano varie regole <xref:System.Object.Equals%2A> correlate a <xref:System.IComparable> e all'interfaccia.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Il codice dell'applicazione seguente verifica il comportamento dell' <xref:System.IComparable> implementazione mostrata in precedenza.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)