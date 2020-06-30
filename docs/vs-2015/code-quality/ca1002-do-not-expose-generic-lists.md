---
title: 'CA1002: non esporre elenchi generici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6fcc4ae2a07eb7b1f155d6c65020e2c1a9ddc9f2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546848"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Non esporre elenchi generici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un membro visibile esternamente che è un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo, restituisce un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo o la cui firma include un <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametro.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>è una raccolta generica progettata per le prestazioni e non per l'ereditarietà. <xref:System.Collections.Generic.List%601?displayProperty=fullName>non contiene membri virtuali che semplificano la modifica del comportamento di una classe ereditata. Le raccolte generiche seguenti sono progettate per l'ereditarietà e devono essere esposte anziché <xref:System.Collections.Generic.List%601?displayProperty=fullName> .

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo in una delle raccolte generiche progettate per l'ereditarietà.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola a meno che l'assembly che genera questo avviso non sia destinato a essere una libreria riutilizzabile. È ad esempio possibile che l'avviso non venga eliminato in un'applicazione ottimizzata per le prestazioni, in cui è stato ottenuto un vantaggio in merito alle prestazioni dall'utilizzo di elenchi generici.

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
