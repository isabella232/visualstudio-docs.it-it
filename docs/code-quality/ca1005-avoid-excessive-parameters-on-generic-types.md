---
title: 'CA1005: Evitare un uso eccessivo di parametri nei tipi generici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34f9b8a79e38bdb9b6b097588697e2cd6c3545f7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236599"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evitare un uso eccessivo di parametri nei tipi generici

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo generico visibile esternamente ha più di due parametri di tipo.

## <a name="rule-description"></a>Descrizione della regola
Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro. È in genere ovvio con un parametro di tipo, come `List<T>`in, e in alcuni casi con due parametri di tipo, `Dictionary<TKey, TValue>`come in. Se esistono più di due parametri di tipo, la difficoltà diventa troppo grande per la maggior parte degli utenti `TooManyTypeParameters<T, K, V>` ( C# ad `TooManyTypeParameters(Of T, K, V)` esempio [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], in o in).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare la progettazione in modo da non utilizzare più di due parametri di tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non eliminare un avviso da questa regola a meno che la progettazione non richieda assolutamente più di due parametri di tipo. Fornire generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario per apprendere e aumentare la velocità di adozione delle nuove librerie.

## <a name="related-rules"></a>Regole correlate
[CA1010 Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000 Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002 Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006 Non annidare tipi generici nelle firme membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004 I metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usare i generics laddove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
[Generics](/dotnet/csharp/programming-guide/generics/index)