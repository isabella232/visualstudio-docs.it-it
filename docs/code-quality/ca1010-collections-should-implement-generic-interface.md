---
title: "CA1010: Le raccolte devono implementare un'interfaccia generica"
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70a418b211cd4340dba9c15f0bf52e3cdfdf8e8f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547910"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Le raccolte devono implementare un'interfaccia generica

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo implementa l' <xref:System.Collections.IEnumerable?displayProperty=fullName> interfaccia ma non implementa l' <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaccia e l'assembly contenitore è destinato a .NET. Questa regola ignora i tipi che implementano <xref:System.Collections.IDictionary?displayProperty=fullName>.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolta generiche. La raccolta può quindi essere usata per popolare i tipi di raccolta generici, come i seguenti:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, implementare una delle interfacce di raccolta generiche seguenti:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola in modo sicuro; Tuttavia, l'uso della raccolta sarà più limitato.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Violazione di esempio

Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che deriva dalla classe non `CollectionBase` generica, che viola questa regola.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Per correggere una violazione di questa regola, effettuare una delle operazioni seguenti:

- Implementare le interfacce generiche.
- Modificare la classe base in un tipo che implementa già le interfacce generiche e non generiche, ad esempio la `Collection<T>` classe.

## <a name="fix-by-base-class-change"></a>Correzione per modifica della classe di base

Nell'esempio seguente viene corretta la violazione modificando la classe di base della raccolta dalla classe non generica `CollectionBase` alla classe generica`Collection(Of T)` `Collection<T>` (in Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

La modifica della classe di base di una classe già rilasciata viene considerata una modifica di rilievo per i consumer esistenti.

## <a name="fix-by-interface-implementation"></a>Correzione dall'implementazione dell'interfaccia

Nell'esempio seguente viene corretta la violazione implementando queste interfacce generiche `ICollection<T>`: `IEnumerable<T>`, `IList<T>` e`IEnumerable(Of T)`( `ICollection(Of T)`, e `IList(Of T)` in Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1005 Evitare parametri eccessivi nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000 Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Non annidare tipi generici nelle firme membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 I metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Usare i generics laddove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

- [Generics](/dotnet/csharp/programming-guide/generics/index)