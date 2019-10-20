---
title: "CA1010: le raccolte devono implementare un'interfaccia generica | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 20238a844b45221207ca952d90d172ac720136ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655245"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Le raccolte devono implementare un'interfaccia generica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente implementa l'interfaccia <xref:System.Collections.IEnumerable?displayProperty=fullName> ma non implementa l'interfaccia <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> e l'assembly contenitore [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]. Questa regola ignora i tipi che implementano <xref:System.Collections.IDictionary?displayProperty=fullName>.

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola in modo sicuro; Tuttavia, la raccolta avrà un uso più limitato.

## <a name="example-violation"></a>Violazione di esempio

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che deriva dalla classe non generica `CollectionBase`, che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Comments
 Per correggere una violazione di questa violazione, è necessario implementare le interfacce generiche o modificare la classe di base in un tipo che implementa già le interfacce generiche e non generiche, ad esempio la classe `Collection<T>`.

## <a name="fix-by-base-class-change"></a>Correzione per modifica della classe di base

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene corretta la violazione modificando la classe di base della raccolta dalla classe `CollectionBase` non generica alla classe generica `Collection<T>` (`Collection(Of T)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Comments
 La modifica della classe di base di una classe già rilasciata viene considerata una modifica di rilievo per i consumer esistenti.

## <a name="fix-by-interface-implementation"></a>Correzione dall'implementazione dell'interfaccia

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene corretta la violazione implementando queste interfacce generiche: `IEnumerable<T>`, `ICollection<T>` e `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)` e `IList(Of T)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
