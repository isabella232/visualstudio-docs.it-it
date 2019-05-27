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
ms.openlocfilehash: 5ebfa5e9b90951acf59c8214941b93adae76d06e
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177381"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Contrassegnare tutti i campi non serializzabili

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.

## <a name="rule-description"></a>Descrizione della regola

Un tipo serializzabile è quello contrassegnato con il <xref:System.SerializableAttribute?displayProperty=fullName> attributo. Quando viene serializzato il tipo, una <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> eccezione viene generata se il tipo contiene un campo di istanza di un tipo che non è serializzabile *e* non implementa il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia.

> [!TIP]
> CA2235 non viene generato, ad esempio i campi di tipi che implementano <xref:System.Runtime.Serialization.ISerializable> perché forniscono la propria logica di serializzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, si applicano le <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo sul campo che non è serializzabile.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare solo un avviso da questa regola se un <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo viene dichiarato che consente alle istanze del campo da serializzare e deserializzare.

## <a name="example"></a>Esempio

L'esempio seguente mostra due tipi: uno che viola la regola e uno che soddisfa la regola.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Note

Regola CA2235 non analizza i tipi che implementano il <xref:System.Runtime.Serialization.ISerializable> interface (a meno che non sono contrassegnati anche con il <xref:System.SerializableAttribute> attributo). Infatti [regola CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) già consiglia contrassegnare i tipi che implementano le <xref:System.Runtime.Serialization.ISerializable> interfacciarsi con il <xref:System.SerializableAttribute> attributo.

## <a name="related-rules"></a>Regole correlate

- [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)