---
title: 'CA2240: Implementare ISerializable in modo corretto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1a6d9acc3a74505f766fbf9cfe26fc6878fdbb4b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920040"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementare ISerializable in modo corretto

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un tipo visibile esternamente è assegnabile all' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e viene soddisfatta una delle condizioni seguenti:

- Il tipo eredita ma non esegue l'override <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> del metodo e il tipo dichiara i campi di istanza che non sono contrassegnati <xref:System.NonSerializedAttribute?displayProperty=fullName> con l'attributo.

- Il tipo non è sealed e il tipo implementa <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> un metodo non visibile esternamente e sottoponibile a override.

## <a name="rule-description"></a>Descrizione della regola
I campi di istanza dichiarati in un tipo che <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> eredita l'interfaccia non vengono inclusi automaticamente nel processo di serializzazione. Per includere i campi, il tipo deve implementare il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo e il costruttore di serializzazione. Se i campi non devono essere serializzati, applicare l' <xref:System.NonSerializedAttribute> attributo ai campi per indicare in modo esplicito la decisione.

Nei tipi non sealed, le <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> implementazioni del metodo devono essere visibili esternamente. Pertanto, il metodo può essere chiamato da tipi derivati ed è sottoponibile a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rendere visibile <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> e sottoponibile a override il metodo e verificare che tutti i campi di istanza siano inclusi nel processo di serializzazione <xref:System.NonSerializedAttribute> o contrassegnati in modo esplicito con l'attributo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrati due tipi serializzabili che violano la regola.

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Esempio
Nell'esempio seguente vengono risolte le due violazioni precedenti fornendo un'implementazione sottoponibile a <xref:System.Runtime.Serialization.ISerializable.GetObjectData> override di nella classe Book e fornendo un'implementazione di `GetObjectData` nella classe della libreria.

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Costruttori di serializzazione protetti](../code-quality/ca2120-secure-serialization-constructors.md)