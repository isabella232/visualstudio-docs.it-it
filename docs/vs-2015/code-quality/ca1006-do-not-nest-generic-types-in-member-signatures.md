---
title: 'CA1006: Non annidare tipi generici nelle firme dei membri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2c8c35180bdff0b76ee8a66a5e1d27bfd915016c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694440"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Non annidare tipi generici nelle firme dei membri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un membro visibile esternamente contiene una firma che contiene un argomento tipo annidato.

## <a name="rule-description"></a>Descrizione della regola
 Un argomento di tipo annidato è un argomento di tipo che è anche un tipo generico. Per chiamare un membro la cui firma contiene un argomento tipo annidato, l'utente deve creare un'istanza su un tipo generico e passare il tipo al costruttore di un secondo tipo generico. La sintassi e la procedura necessarie sono complesse ed è opportuno evitarle.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione per rimuovere l'argomento tipo annidato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Che fornisce una sintassi facile da comprendere e usare generics riduce il tempo necessario all'apprendimento e aumenta la frequenza di adozione di nuove librerie.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un metodo che viola la regola e la sintassi necessaria per chiamare il metodo.

 [!code-csharp[FxCop.Design.NestedGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/cs/FxCop.Design.NestedGenerics.cs#1)]
 [!code-vb[FxCop.Design.NestedGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/vb/FxCop.Design.NestedGenerics.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare l'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
