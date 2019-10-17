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
ms.openlocfilehash: 77f913a2dc31ee77445ee90b417f1a7d1cf23b8d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449354"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evitare un uso eccessivo di parametri nei tipi generici

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft. Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo generico visibile esternamente ha più di due parametri di tipo.

## <a name="rule-description"></a>Descrizione della regola
Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro. È in genere ovvio con un parametro di tipo, come in `List<T>`, e in alcuni casi con due parametri di tipo, come in `Dictionary<TKey, TValue>`. Se esistono più di due parametri di tipo, la difficoltà diventa troppo grande per la maggior parte degli utenti (ad esempio, C# `TooManyTypeParameters<T, K, V>` in o `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, modificare la progettazione in modo da non utilizzare più di due parametri di tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non eliminare un avviso da questa regola a meno che la progettazione non richieda assolutamente più di due parametri di tipo. Fornire generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario per apprendere e aumentare la velocità di adozione delle nuove librerie.

## <a name="related-rules"></a>Regole correlate
[CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
[Generics](/dotnet/csharp/programming-guide/generics/index)
