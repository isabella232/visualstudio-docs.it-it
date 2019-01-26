---
title: 'CA1038: Gli enumeratori devono essere fortemente tipizzati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f103a100474a1c52a5dd5da2f0403d160df37e46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932922"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Gli enumeratori devono essere fortemente tipizzati

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> ma non fornisce una versione fortemente tipizzata del <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> proprietà. I tipi derivati dai seguenti tipi sono esclusi da questa regola:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Questa regola richiede <xref:System.Collections.IEnumerator> implementazioni forniscano anche una versione fortemente tipizzata del <xref:System.Collections.IEnumerator.Current%2A> proprietà in modo che gli utenti non è necessario eseguire il cast del valore restituito al tipo sicuro quando utilizzano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IEnumerator> contiene una raccolta di istanze di un tipo più sicuro <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementa la proprietà dell'interfaccia in modo esplicito (dichiararla come `IEnumerator.Current`). Aggiungere una versione pubblica fortemente tipizzata della proprietà, dichiarata come `Current`, e attendere che restituisca un oggetto fortemente tipizzato.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola quando si implementa un enumeratore e basato sugli oggetti per l'uso con una raccolta basata su oggetti, ad esempio un albero binario. I tipi che estendono la nuova raccolta verranno definire l'enumeratore fortemente tipizzato ed espongono la proprietà fortemente tipizzata.

## <a name="example"></a>Esempio
 L'esempio seguente illustra il modo corretto per implementare una classe fortemente tipizzata <xref:System.Collections.IEnumerator> tipo.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>