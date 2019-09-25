---
title: 'CA2235: Contrassegnare tutti i campi non serializzabili'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238107"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Contrassegnare tutti i campi non serializzabili

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.

## <a name="rule-description"></a>Descrizione della regola

Un tipo serializzabile è un tipo contrassegnato con l' <xref:System.SerializableAttribute?displayProperty=fullName> attributo. Quando il tipo viene serializzato, viene <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> generata un'eccezione se il tipo contiene un campo di istanza di un tipo che non è serializzabile *e* non <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> implementa l'interfaccia.

> [!TIP]
> CA2235 non viene attivato per i campi di istanza dei tipi <xref:System.Runtime.Serialization.ISerializable> che implementano perché forniscono una propria logica di serializzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, applicare l' <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo al campo non serializzabile.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Eliminare un avviso da questa regola solo se viene <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> dichiarato un tipo che consente la serializzazione e la deserializzazione delle istanze del campo.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati due tipi: uno che viola la regola e uno che soddisfa la regola.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Note

La regola CA2235 non analizza i tipi che implementano l' <xref:System.Runtime.Serialization.ISerializable> interfaccia (a meno che non siano contrassegnati anche con l' <xref:System.SerializableAttribute> attributo). Questo perché la [regola CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) consiglia già di contrassegnare i tipi che <xref:System.Runtime.Serialization.ISerializable> implementano l' <xref:System.SerializableAttribute> interfaccia con l'attributo.

## <a name="related-rules"></a>Regole correlate

- [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240 Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Costruttori di serializzazione protetti](../code-quality/ca2120-secure-serialization-constructors.md)