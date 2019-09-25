---
title: 'CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237935"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo visibile esternamente implementa l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e il tipo non è contrassegnato con l' <xref:System.SerializableAttribute?displayProperty=fullName> attributo. La regola ignora i tipi derivati il cui tipo di base non è serializzabile.

## <a name="rule-description"></a>Descrizione della regola
Per essere riconosciuti dal Common Language Runtime come serializzabile, i tipi devono essere contrassegnati <xref:System.SerializableAttribute> con l'attributo anche se il tipo usa una routine <xref:System.Runtime.Serialization.ISerializable> di serializzazione personalizzata tramite l'implementazione dell'interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, applicare l' <xref:System.SerializableAttribute> attributo al tipo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non eliminare un avviso da questa regola per le classi di eccezione perché devono essere serializzabili per funzionare correttamente tra domini dell'applicazione.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola la regola. Rimuovere il commento <xref:System.SerializableAttribute> dalla riga dell'attributo per soddisfare la regola.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240 Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Costruttori di serializzazione protetti](../code-quality/ca2120-secure-serialization-constructors.md)