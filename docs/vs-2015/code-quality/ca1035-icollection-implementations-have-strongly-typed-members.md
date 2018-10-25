---
title: 'CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c5a20352b92c5cf4089029d9b613fdf8a83a8c2e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930154"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa <xref:System.Collections.ICollection?displayProperty=fullName> ma non fornisce un metodo fortemente tipizzato per <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. La versione fortemente tipizzata della <xref:System.Collections.ICollection.CopyTo%2A> deve accettare due parametri e non può contenere un <xref:System.Array?displayProperty=fullName> o una matrice di <xref:System.Object?displayProperty=fullName> come primo parametro.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola richiede <xref:System.Collections.ICollection> membri implementazioni per fornire fortemente tipizzati in modo che gli utenti non è necessario eseguire il cast di argomenti per il <xref:System.Object> digitare quando usano la funzionalità fornita dall'interfaccia. Questa regola presuppone che il tipo che implementa <xref:System.Collections.ICollection> esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro <xref:System.Object>.

 L'oggetto <xref:System.Collections.ICollection> implementa l'interfaccia <xref:System.Collections.IEnumerable?displayProperty=fullName>. Se gli oggetti nella raccolta estendono <xref:System.ValueType?displayProperty=fullName>, è necessario fornire un membro fortemente tipizzato per <xref:System.Collections.IEnumerable.GetEnumerator%2A> per evitare un calo delle prestazioni causata dalla conversione boxing. Ciò non è necessario quando gli oggetti della raccolta sono un tipo di riferimento.

 Per implementare una versione fortemente tipizzata di un membro di interfaccia, implementare i membri di interfaccia in modo esplicito usando nomi nel formato `InterfaceName.InterfaceMemberName`, ad esempio <xref:System.Collections.ICollection.CopyTo%2A>. I membri di interfaccia esplicita utilizzano i tipi di dati che vengono dichiarati dall'interfaccia. Implementare i membri fortemente tipizzati usando il nome di membro di interfaccia, ad esempio <xref:System.Collections.ICollection.CopyTo%2A>. Dichiarare i membri fortemente tipizzati come pubblici e dichiarare i parametri e restituire i valori siano del tipo sicuro gestito dalla raccolta. I tipi sicuri sostituiscono, ad esempio tipi più vulnerabili <xref:System.Object> e <xref:System.Array> che vengono dichiarati dall'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il membro di interfaccia in modo esplicito (dichiararla come <xref:System.Collections.ICollection.CopyTo%2A>). Aggiungere il membro pubblico di fortemente tipizzato, dichiarato come `CopyTo`, lasciando che accetta una matrice fortemente tipizzata come primo parametro.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se si implementa una nuova raccolta basata su oggetti, ad esempio un albero binario, in cui i tipi che estendono la nuova raccolta determinano il tipo sicuro. Questi tipi devono conformi a questa regola ed esporre membri fortemente tipizzati.

## <a name="example"></a>Esempio
 L'esempio seguente illustra il modo corretto per implementare <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>



