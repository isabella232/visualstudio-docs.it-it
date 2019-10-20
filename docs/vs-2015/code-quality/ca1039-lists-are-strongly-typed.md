---
title: 'CA1039: gli elenchi sono fortemente tipizzati | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8845fb8bcd08f076ddc3c509a37948cf008e0623
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661805"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Gli elenchi sono fortemente tipizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Il tipo pubblico o protetto implementa <xref:System.Collections.IList?displayProperty=fullName>, ma non fornisce un metodo fortemente tipizzato per uno o più degli elementi seguenti:

- IList. Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Descrizione della regola
 Questa regola richiede che le implementazioni di <xref:System.Collections.IList> forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo di <xref:System.Object?displayProperty=fullName> quando utilizzano la funzionalità fornita dall'interfaccia. L'interfaccia <xref:System.Collections.IList> è implementata da raccolte di oggetti a cui è possibile accedere tramite indice. Questa regola presuppone che il tipo che implementa <xref:System.Collections.IList> esegue questa operazione per gestire una raccolta di istanze di un tipo più forte rispetto a <xref:System.Object>.

 <xref:System.Collections.IList> implementa le interfacce <xref:System.Collections.ICollection?displayProperty=fullName> e <xref:System.Collections.IEnumerable?displayProperty=fullName>. Se si implementa <xref:System.Collections.IList>, è necessario fornire i membri fortemente tipizzati necessari per <xref:System.Collections.ICollection>. Se gli oggetti nella raccolta si estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> per evitare la riduzione delle prestazioni causata dalla conversione boxing; Questa operazione non è necessaria se gli oggetti della raccolta sono un tipo di riferimento.

 Per garantire la conformità a questa regola, implementare i membri di interfaccia in modo esplicito usando nomi nel formato InterfaceName. NomeMembroInterfaccia, ad esempio <xref:System.Collections.IList.Add%2A>. I membri di interfaccia espliciti usano i tipi di dati dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati utilizzando il nome del membro di interfaccia, ad esempio `Add`. Dichiarare i membri fortemente tipizzati come Public e dichiarare i parametri e i valori restituiti in modo che siano del tipo sicuro gestito dalla raccolta. I tipi Strong sostituiscono i tipi più vulnerabili, ad esempio <xref:System.Object> e <xref:System.Array> dichiarati dall'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare in modo esplicito i membri <xref:System.Collections.IList> e fornire alternative fortemente tipizzate per i membri che sono stati annotati in precedenza. Per il codice che implementa correttamente l'interfaccia <xref:System.Collections.IList> e fornisce i membri fortemente tipizzati richiesti, vedere l'esempio seguente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola quando si implementa una nuova raccolta basata su oggetti, ad esempio un elenco collegato, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro. Questi tipi devono essere conformi a questa regola ed esporre membri fortemente tipizzati.

## <a name="example"></a>Esempio
 Nell'esempio seguente, il tipo `YourType` estende <xref:System.Collections.CollectionBase?displayProperty=fullName>, come per tutte le raccolte fortemente tipizzate. Si noti che <xref:System.Collections.CollectionBase> fornisce l'implementazione esplicita dell'interfaccia <xref:System.Collections.IList> per l'utente. Pertanto, è necessario fornire solo i membri fortemente tipizzati per <xref:System.Collections.IList> e <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
