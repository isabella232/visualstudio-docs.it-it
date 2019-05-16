---
title: 'CA1002: Non esporre elenchi generici | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2d1b4f67f25db7c0006decc5fc26696c6c5dad01
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685345"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Non esporre elenchi generici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un membro visibile esternamente che è un <xref:System.Collections.Generic.List%601?displayProperty=fullName> digita, restituisce un <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo o la cui firma include un <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametro.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> è una raccolta generica che è progettata per prestazioni e non per l'ereditarietà. <xref:System.Collections.Generic.List%601?displayProperty=fullName> non contiene membri virtuali che rendono più semplice modificare il comportamento di una classe ereditata. Le raccolte generiche seguenti sono progettate per l'ereditarietà e devono essere esposte al posto di <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare il <xref:System.Collections.Generic.List%601?displayProperty=fullName> tipo su uno degli insiemi generici che è progettato per l'ereditarietà.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola, a meno che l'assembly che ha generato l'avviso non deve essere una libreria riutilizzabile. Ad esempio, sarebbe possibile eliminare l'avviso in un'applicazione di ottimizzarne le prestazioni in cui è stato ottenuto un miglioramento delle prestazioni dall'utilizzo di elenchi generici.

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare l'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
