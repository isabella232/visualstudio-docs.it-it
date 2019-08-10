---
title: 'CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a20feb514b87f2906fd4db32dfb38d3d9b661999
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922823"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un tipo pubblico o protetto implementa <xref:System.Collections.ICollection?displayProperty=fullName> ma non fornisce un metodo fortemente tipizzato per <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. La versione fortemente tipizzata <xref:System.Collections.ICollection.CopyTo%2A> di deve accettare due parametri e non può <xref:System.Array?displayProperty=fullName> avere un oggetto o <xref:System.Object?displayProperty=fullName> una matrice di come primo parametro.

## <a name="rule-description"></a>Descrizione della regola
Questa regola richiede <xref:System.Collections.ICollection> che le implementazioni forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto <xref:System.Object> di eseguire il cast di argomenti al tipo quando usano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.ICollection> esegue tale operazione per gestire una raccolta di istanze di un tipo più forte rispetto <xref:System.Object>a.

 L'oggetto <xref:System.Collections.ICollection> implementa l'interfaccia <xref:System.Collections.IEnumerable?displayProperty=fullName>. Se gli oggetti nella raccolta si estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> per evitare la riduzione delle prestazioni causata dalla conversione boxing. Questa operazione non è necessaria se gli oggetti della raccolta sono un tipo di riferimento.

Per implementare una versione fortemente tipizzata di un membro di interfaccia, implementare i membri di interfaccia in modo esplicito usando `InterfaceName.InterfaceMemberName`nomi nel formato <xref:System.Collections.ICollection.CopyTo%2A>, ad esempio. I membri di interfaccia espliciti usano i tipi di dati dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati utilizzando il nome del membro di interfaccia, <xref:System.Collections.ICollection.CopyTo%2A>ad esempio. Dichiarare i membri fortemente tipizzati come Public e dichiarare i parametri e i valori restituiti in modo che siano del tipo sicuro gestito dalla raccolta. I tipi Strong sostituiscono i tipi più vulnerabili <xref:System.Object> , <xref:System.Array> ad esempio e, dichiarati dall'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, implementare il membro di interfaccia in modo esplicito ( <xref:System.Collections.ICollection.CopyTo%2A>dichiararlo come). Aggiungere il membro pubblico fortemente tipizzato, dichiarato `CopyTo`come e richiedere una matrice fortemente tipizzata come primo parametro.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola se si implementa una nuova raccolta basata su oggetti, ad esempio un albero binario, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro. Questi tipi devono essere conformi a questa regola ed esporre membri fortemente tipizzati.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato il modo corretto per <xref:System.Collections.ICollection>implementare.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>