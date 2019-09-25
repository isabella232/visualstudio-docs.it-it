---
title: 'CA1039: Gli elenchi sono fortemente tipizzati'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcc399457f4dde1c65836d9c9498c782ba92ecc2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235980"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Gli elenchi sono fortemente tipizzati

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il tipo pubblico o protetto implementa <xref:System.Collections.IList?displayProperty=fullName> ma non fornisce un metodo fortemente tipizzato per uno o più degli elementi seguenti:

- IList. Item

- IList. Add

- IList. Contains

- IList.IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Descrizione della regola

Questa regola richiede <xref:System.Collections.IList> che le implementazioni forniscano membri fortemente tipizzati, in modo che gli utenti non debbano <xref:System.Object?displayProperty=fullName> eseguire il cast di argomenti al tipo quando usano la funzionalità fornita dall'interfaccia. L' <xref:System.Collections.IList> interfaccia viene implementata da raccolte di oggetti a cui è possibile accedere tramite indice. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IList> gestisca una raccolta di istanze di un tipo più forte rispetto <xref:System.Object>a.

<xref:System.Collections.IList>implementa le <xref:System.Collections.ICollection?displayProperty=fullName> interfacce <xref:System.Collections.IEnumerable?displayProperty=fullName> e. Se si implementa <xref:System.Collections.IList>, è necessario fornire i membri fortemente tipizzati necessari <xref:System.Collections.ICollection>per. Se gli oggetti nella raccolta si estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> per evitare la riduzione delle prestazioni causata dalla conversione boxing. questa operazione non è necessaria se gli oggetti della raccolta sono un tipo di riferimento.

Per conformarsi a questa regola, implementare i membri di interfaccia in modo esplicito usando i nomi nel formato interfacet. NomeMembroInterfaccia, ad <xref:System.Collections.IList.Add%2A>esempio. I membri di interfaccia espliciti usano i tipi di dati dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati utilizzando il nome del membro di interfaccia, `Add`ad esempio. Dichiarare i membri fortemente tipizzati come Public e dichiarare i parametri e i valori restituiti in modo che siano del tipo sicuro gestito dalla raccolta. I tipi Strong sostituiscono i tipi più vulnerabili <xref:System.Object> , <xref:System.Array> ad esempio e, dichiarati dall'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, implementare <xref:System.Collections.IList> in modo esplicito i membri e fornire alternative fortemente tipizzate per i membri che sono stati annotati in precedenza. Per il codice che implementa correttamente <xref:System.Collections.IList> l'interfaccia e fornisce i membri fortemente tipizzati richiesti, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Eliminare un avviso da questa regola quando si implementa una nuova raccolta basata su oggetti, ad esempio un elenco collegato, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro. Questi tipi devono essere conformi a questa regola ed esporre membri fortemente tipizzati.

## <a name="example"></a>Esempio
Nell'esempio seguente, il tipo `YourType` estende <xref:System.Collections.CollectionBase?displayProperty=fullName>, perché tutte le raccolte fortemente tipizzate dovrebbero. <xref:System.Collections.CollectionBase>fornisce l'implementazione esplicita dell' <xref:System.Collections.IList> interfaccia. Pertanto, è necessario fornire solo i membri fortemente tipizzati <xref:System.Collections.IList> per <xref:System.Collections.ICollection>e.

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>