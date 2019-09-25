---
title: 'CA2238: Implementare correttamente i metodi di serializzazione'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b0bbe31f0431b259f60c1fe68a8d9edeffc572d9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237915"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementare correttamente i metodi di serializzazione

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Category|Microsoft.Usage|
|Modifica|Interruzioni: se il metodo è visibile all'esterno dell'assembly.<br /><br /> Senza interruzioni: se il metodo non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
Un metodo che gestisce un evento di serializzazione non dispone della visibilità, del tipo restituito o della firma corretta.

## <a name="rule-description"></a>Descrizione della regola
Un metodo viene designato come gestore eventi di serializzazione applicando uno degli attributi dell'evento di serializzazione seguenti:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  I gestori eventi di serializzazione accettano un solo parametro <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>di tipo `void`, restituiscono `private` e hanno visibilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, correggere la firma, il tipo restituito o la visibilità del gestore eventi di serializzazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrati i gestori eventi di serializzazione dichiarati correttamente.

[!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
[!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240 Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Costruttori di serializzazione protetti](../code-quality/ca2120-secure-serialization-constructors.md)