---
title: "CA1010: Le raccolte devono implementare un'interfaccia generica | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8e0ae778101d39f5a476c56760d1ce8824f33c4d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589986"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Le raccolte devono implementare un'interfaccia generica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1010: le raccolte devono implementare l'interfaccia generica](https://docs.microsoft.com/visualstudio/code-quality/ca1010-collections-should-implement-generic-interface).

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Implementa un tipo visibile esternamente il <xref:System.Collections.IEnumerable?displayProperty=fullName> dell'interfaccia, ma non implementa le <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfaccia e l'assembly che lo contiene è destinato [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]. Questa regola ignora i tipi che implementano <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolta generiche. Quindi la raccolta può essere utilizzata per popolare tipi di raccolte generiche, ad esempio il seguente:

-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare una delle interfacce di raccolta generiche seguenti:

-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, la raccolta sarà necessario un utilizzo più limitato.

## <a name="example-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una classe (tipo riferimento) che deriva da non generica `CollectionBase` che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Commenti
 Per correggere una violazione della violazione, si deve implementare le interfacce generiche o modificare la classe di base in un tipo che implementa già entrambe le interfacce generiche e non generici, ad esempio il `Collection<T>` classe.

## <a name="fix-by-base-class-change"></a>Correggere da modifica della classe di Base

### <a name="description"></a>Descrizione
 Nell'esempio seguente la violazione viene corretta modificando la classe di base della raccolta da non generica `CollectionBase` sulla classe generica `Collection<T>` (`Collection(Of T)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) classe.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Commenti
 La classe base di una classe già rilasciata la modifica è considerata una modifica di rilievo per i consumer esistenti.

## <a name="fix-by-interface-implementation"></a>Correggere dall'implementazione dell'interfaccia

### <a name="description"></a>Descrizione
 Nell'esempio seguente la violazione viene corretta mediante l'implementazione di queste interfacce generiche: `IEnumerable<T>`, `ICollection<T>`, e `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, e `IList(Of T)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

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
 [Generics](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



