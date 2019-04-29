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
ms.openlocfilehash: c71912fdd70226e1b4be3c14be7c4e0bac26259d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779846"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Le raccolte devono implementare un'interfaccia generica

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un tipo implementa la <xref:System.Collections.IEnumerable?displayProperty=fullName> dell'interfaccia, ma non implementa il <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaccia e le destinazioni .NET assembly che lo contiene. Questa regola ignora i tipi che implementano <xref:System.Collections.IDictionary?displayProperty=fullName>.

Per impostazione predefinita, questa regola cerca solo tipi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolta generiche. Quindi la raccolta può essere utilizzata per popolare tipi di raccolte generiche, ad esempio il seguente:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, implementare una delle interfacce di raccolta generiche seguenti:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola. Tuttavia, l'uso della raccolta sarà più limitato.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1010.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Esempio di violazione

Nell'esempio seguente viene illustrata una classe (tipo riferimento) che deriva da non generica `CollectionBase` che viola questa regola.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Per correggere una violazione di questa regola, eseguire una delle operazioni seguenti:

- Implementare le interfacce generiche.
- Modificare la classe di base in un tipo che implementa già entrambe le interfacce generiche e non generici, ad esempio il `Collection<T>` classe.

## <a name="fix-by-base-class-change"></a>Correggere da modifica della classe di base

Nell'esempio seguente la violazione viene corretta modificando la classe di base della raccolta da non generica `CollectionBase` sulla classe generica `Collection<T>` (`Collection(Of T)` in Visual Basic) classe.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

La classe base di una classe già rilasciata la modifica è considerata una modifica di rilievo per i consumer esistenti.

## <a name="fix-by-interface-implementation"></a>Correggere dall'implementazione dell'interfaccia

Nell'esempio seguente la violazione viene corretta mediante l'implementazione di queste interfacce generiche: `IEnumerable<T>`, `ICollection<T>`, e `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, e `IList(Of T)` in Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

- [Generics](/dotnet/csharp/programming-guide/generics/index)