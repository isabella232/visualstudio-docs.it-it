---
title: 'CA1000: Non dichiarare membri statici su tipi generici'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4cc33c51af7d596fb9c784b76f8cc2f255ddf5a5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236708"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Non dichiarare membri statici su tipi generici

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo generico contiene un `static` membro`Shared` (in Visual Basic).

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Quando viene `static` chiamato un membro di un tipo generico, è necessario specificare l'argomento di tipo per il tipo. Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento tipo relativo al membro. La sintassi per specificare l'argomento di tipo in questi due casi è diversa e facile da confondere, come illustrato nelle chiamate seguenti:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

In genere, è consigliabile evitare entrambe le dichiarazioni precedenti in modo che l'argomento di tipo non debba essere specificato quando viene chiamato il membro. In questo modo si ottiene una sintassi per chiamare i membri dei generics che non sono diversi dalla sintassi per i tipi non generici. Per ulteriori informazioni, vedere [CA1004: I metodi generici devono fornire](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)il parametro di tipo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il membro statico o impostarlo come membro di istanza.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. Fornire generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario per apprendere e aumentare la velocità di adozione delle nuove librerie.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

- [CA1005 Evitare parametri eccessivi nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010 Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002 Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Non annidare tipi generici nelle firme membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 I metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Usare i generics laddove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

- [Generics](/dotnet/csharp/programming-guide/generics/index)