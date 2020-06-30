---
title: 'CA1000: non dichiarare membri statici su tipi generici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 66bca5b8b039de59509cecf4ecfae6bd6b4f0162
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548330"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Non dichiarare membri statici su tipi generici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo generico visibile esternamente contiene un `static` `Shared` membro (in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 Quando `static` viene chiamato un membro di un tipo generico, è necessario specificare l'argomento di tipo per il tipo. Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento tipo relativo al membro. La sintassi per specificare l'argomento di tipo in questi due casi è diversa e facile da confondere, come illustrato nelle chiamate seguenti:

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

 In genere, è consigliabile evitare entrambe le dichiarazioni precedenti in modo che l'argomento di tipo non debba essere specificato quando viene chiamato il membro. In questo modo si ottiene una sintassi per chiamare i membri dei generics che non sono diversi dalla sintassi per i tipi non generici. Per ulteriori informazioni, vedere [CA1004: i metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il membro statico o impostarlo come membro di istanza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Fornire generics in una sintassi facile da comprendere e utilizzare riduce il tempo necessario per apprendere e aumentare la velocità di adozione delle nuove librerie.

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Usare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
