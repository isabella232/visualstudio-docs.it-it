---
title: 'CA1039: Gli elenchi sono fortemente tipizzati'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 5e5a9f99bb89e78da34860cb5470627bcc5c8574
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980492"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Gli elenchi sono fortemente tipizzati

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Il tipo pubblico o protetto il tipo implementa <xref:System.Collections.IList?displayProperty=fullName> ma non fornisce un metodo fortemente tipizzato per uno o più delle operazioni seguenti:

- IList.Item

- IList

- IList.Contains

- IList.IndexOf

- IList. Insert

- IList.Remove

## <a name="rule-description"></a>Descrizione della regola

Questa regola richiede <xref:System.Collections.IList> implementazioni per fornire fortemente tipizzate membri, in modo che gli utenti non è necessario eseguire il cast di argomenti per il <xref:System.Object?displayProperty=fullName> digitare quando usano la funzionalità fornita dall'interfaccia. Il <xref:System.Collections.IList> viene implementata mediante raccolte di oggetti che è possibile accedere tramite indice. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IList> gestisce una raccolta di istanze di un tipo più sicuro <xref:System.Object>.

<xref:System.Collections.IList> implementa il <xref:System.Collections.ICollection?displayProperty=fullName> e <xref:System.Collections.IEnumerable?displayProperty=fullName> interfacce. Se si implementa <xref:System.Collections.IList>, è necessario fornire i membri necessari fortemente tipizzati per <xref:System.Collections.ICollection>. Se gli oggetti nella raccolta estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> di evitare un calo nelle prestazioni causato dalla conversione boxing; non è obbligatorio quando gli oggetti della raccolta sono un tipo di riferimento.

Per garantire la conformità con questa regola, implementare i membri di interfaccia in modo esplicito usando nomi nel formato InterfaceName, ad esempio <xref:System.Collections.IList.Add%2A>. I membri di interfaccia esplicita utilizzano i tipi di dati che vengono dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati usando il nome di membro di interfaccia, ad esempio `Add`. Dichiarare i membri fortemente tipizzati come pubblici e dichiarare i parametri e restituire i valori siano del tipo sicuro gestito dalla raccolta. I tipi sicuri sostituiscono, ad esempio tipi più vulnerabili <xref:System.Object> e <xref:System.Array> che vengono dichiarati dall'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare in modo esplicito <xref:System.Collections.IList> membri e offrono alternative fortemente tipizzate per i membri che sono stati annotati in precedenza. Per il codice che implementa correttamente il <xref:System.Collections.IList> interfaccia e offre la necessaria membri fortemente tipizzati, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola quando si implementa una nuova raccolta basata su oggetti, ad esempio un elenco collegato, in cui i tipi che estendono la nuova raccolta determinano la tipizzazione forte. Questi tipi devono conformi a questa regola ed esporre membri fortemente tipizzati.

## <a name="example"></a>Esempio
 Nell'esempio seguente, il tipo `YourType` estende <xref:System.Collections.CollectionBase?displayProperty=fullName>, come avviene per tutte le raccolte fortemente tipizzate. <xref:System.Collections.CollectionBase> fornisce l'implementazione esplicita del <xref:System.Collections.IList> interfaccia per l'utente. Pertanto, è necessario fornire solo i membri fortemente tipizzati per <xref:System.Collections.IList> e <xref:System.Collections.ICollection>.

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