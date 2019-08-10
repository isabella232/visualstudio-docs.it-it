---
title: 'CA1038: Gli enumeratori devono essere fortemente tipizzati'
ms.date: 11/04/2016
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
ms.openlocfilehash: 2dae77bf7783edc165305f9b3ba60969d4f126a8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922898"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Gli enumeratori devono essere fortemente tipizzati

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un tipo pubblico o protetto implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> ma non fornisce una versione fortemente tipizzata <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> della proprietà. I tipi derivati dai seguenti tipi sono esenti da questa regola:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
Questa regola richiede <xref:System.Collections.IEnumerator> che le implementazioni forniscano anche una versione fortemente tipizzata <xref:System.Collections.IEnumerator.Current%2A> della proprietà, in modo che gli utenti non debbano eseguire il cast del valore restituito al tipo sicuro quando usano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IEnumerator> contenga una raccolta di istanze di un tipo maggiore di <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, implementare in modo esplicito la proprietà dell'interfaccia ( `IEnumerator.Current`dichiararla come). Aggiungere una versione fortemente tipizzata pubblica della proprietà, dichiarata come e fare in `Current`modo che restituisca un oggetto fortemente tipizzato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola quando si implementa un enumeratore basato su oggetti da usare con una raccolta basata su oggetti, ad esempio un albero binario. I tipi che estendono la nuova raccolta definiranno l'enumeratore fortemente tipizzato ed esporrà la proprietà fortemente tipizzata.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato il modo corretto per implementare un tipo <xref:System.Collections.IEnumerator> fortemente tipizzato.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>