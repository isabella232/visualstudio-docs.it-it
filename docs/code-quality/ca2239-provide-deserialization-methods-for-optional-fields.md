---
title: 'CA2239: Fornire metodi di deserializzazione per i campi facoltativi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 572bf56c63e8fcbf9d78738d7cdffcf9540df158
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988964"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Fornire metodi di deserializzazione per i campi facoltativi

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo ha un campo contrassegnato con il <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> attributo e il tipo non fornisce i metodi di gestione degli eventi di deserializzazione.

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.Runtime.Serialization.OptionalFieldAttribute> attributo non ha alcun effetto sulla serializzazione; viene serializzato un campo contrassegnato con l'attributo. Tuttavia, il campo viene ignorato durante la deserializzazione e mantiene il valore predefinito associato al relativo tipo. I gestori di eventi di deserializzazione devono essere dichiarati per impostare il campo durante il processo di deserializzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere i metodi per il tipo di gestione degli eventi di deserializzazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se il campo deve essere ignorato durante il processo di deserializzazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo con un campo facoltativo e un evento di deserializzazione metodi di gestione.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)