---
title: 'CA1006: Non annidare tipi generici nelle firme dei membri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45ff4831875150df02d04553e75cebcab9a9f572
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236511"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Non annidare tipi generici nelle firme dei membri

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un membro visibile esternamente ha una firma contenente un argomento di tipo annidato.

## <a name="rule-description"></a>Descrizione della regola
Un argomento di tipo annidato è un argomento di tipo che è anche un tipo generico. Per chiamare un membro la cui firma contiene un argomento tipo annidato, l'utente deve creare un'istanza su un tipo generico e passare il tipo al costruttore di un secondo tipo generico. La sintassi e la procedura necessarie sono complesse ed è opportuno evitarle.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare la progettazione per rimuovere l'argomento di tipo annidato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Fornire generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario per apprendere e aumentare la velocità di adozione delle nuove librerie.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un metodo che viola la regola e la sintassi necessaria per chiamare il metodo violato.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1005 Evitare parametri eccessivi nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010 Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004 I metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usare i generics laddove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
[Generics](/dotnet/csharp/programming-guide/generics/index)