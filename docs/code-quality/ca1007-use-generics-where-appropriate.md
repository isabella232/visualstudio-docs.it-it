---
title: 'CA1007: Utilizzare generics dove appropriato'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d2c9416d1cdc655df110c7230b9f0e29290221a7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441696"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Utilizzare generics dove appropriato

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Category|Microsoft. Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un metodo visibile esternamente contiene un parametro di riferimento di tipo <xref:System.Object?displayProperty=fullName> e l'assembly contenitore ha come destinazione .NET Framework 2,0.

## <a name="rule-description"></a>Descrizione della regola
Un parametro di riferimento è un parametro modificato tramite la parola chiave `ref` (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Il tipo di argomento fornito per un parametro di riferimento deve corrispondere esattamente al tipo di parametro di riferimento. Per usare un tipo derivato dal tipo di parametro Reference, è necessario prima eseguire il cast del tipo e assegnarlo a una variabile del tipo di parametro Reference. L'uso di un metodo generico consente di passare al metodo tutti i tipi, soggetti a vincoli, senza prima eseguire il cast del tipo al tipo di parametro di riferimento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rendere generico il metodo e sostituire il parametro <xref:System.Object> usando un parametro di tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrata una routine di scambio di utilizzo generico implementata come metodi non generici e generici. Si noti il modo in cui le stringhe vengono scambiate usando il metodo generico rispetto al metodo non generico.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Vedere anche
[Generics](/dotnet/csharp/programming-guide/generics/index)
