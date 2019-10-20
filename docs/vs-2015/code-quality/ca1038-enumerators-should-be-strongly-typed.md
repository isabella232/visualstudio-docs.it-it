---
title: 'CA1038: gli enumeratori devono essere fortemente tipizzati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661761"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Gli enumeratori devono essere fortemente tipizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> ma non fornisce una versione fortemente tipizzata della proprietà <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>. I tipi derivati dai seguenti tipi sono esenti da questa regola:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Questa regola richiede che le implementazioni di <xref:System.Collections.IEnumerator> forniscano anche una versione fortemente tipizzata della proprietà <xref:System.Collections.IEnumerator.Current%2A>, in modo che gli utenti non debbano eseguire il cast del valore restituito al tipo sicuro quando usano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IEnumerator> contenga una raccolta di istanze di un tipo più forte di <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare in modo esplicito la proprietà dell'interfaccia (dichiararla come `IEnumerator.Current`). Aggiungere una versione fortemente tipizzata pubblica della proprietà, dichiarata come `Current` e fare in modo che restituisca un oggetto fortemente tipizzato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola quando si implementa un enumeratore basato su oggetti da usare con una raccolta basata su oggetti, ad esempio un albero binario. I tipi che estendono la nuova raccolta definiranno l'enumeratore fortemente tipizzato ed esporrà la proprietà fortemente tipizzata.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato il modo corretto per implementare un tipo <xref:System.Collections.IEnumerator> fortemente tipizzato.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
