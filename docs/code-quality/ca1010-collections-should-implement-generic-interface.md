---
title: "CA1010: Le raccolte devono implementare un'interfaccia generica"
ms.date: 11/04/2016
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
ms.openlocfilehash: 9998f54298107ce7a6fb31cf6eb8481998ddfbae
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955865"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Le raccolte devono implementare un'interfaccia generica

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Implementa un tipo visibile esternamente il <xref:System.Collections.IEnumerable?displayProperty=fullName> dell'interfaccia, ma non implementa le <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaccia e l'assembly che lo contiene è destinato [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Questa regola ignora i tipi che implementano <xref:System.Collections.IDictionary?displayProperty=fullName>.

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
 È possibile eliminare un avviso da questa regola. Tuttavia, la raccolta sarà necessario un utilizzo più limitato.

## <a name="example-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una classe (tipo riferimento) che deriva da non generica `CollectionBase` che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Commenti
 Per correggere una violazione della violazione, si deve implementare le interfacce generiche o modificare la classe di base in un tipo che implementa già entrambe le interfacce generiche e non generici, ad esempio il `Collection<T>` classe.

## <a name="fix-by-base-class-change"></a>Correggere da modifica della classe di Base

### <a name="description"></a>Descrizione
 Nell'esempio seguente la violazione viene corretta modificando la classe di base della raccolta da non generica `CollectionBase` sulla classe generica `Collection<T>` (`Collection(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) classe.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Commenti
 La classe base di una classe già rilasciata la modifica è considerata una modifica di rilievo per i consumer esistenti.

## <a name="fix-by-interface-implementation"></a>Correggere dall'implementazione dell'interfaccia

### <a name="description"></a>Descrizione
 Nell'esempio seguente la violazione viene corretta mediante l'implementazione di queste interfacce generiche: `IEnumerable<T>`, `ICollection<T>`, e `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, e `IList(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](/dotnet/csharp/programming-guide/generics/index)