---
title: 'CA2235: Contrassegnare tutti i campi non serializzabili | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcd0c1ddedd57208101df05c0525a35e11b67822
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828923"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Contrassegnare tutti i campi non serializzabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.

## <a name="rule-description"></a>Descrizione della regola
 Un tipo serializzabile è quello contrassegnato con il <xref:System.SerializableAttribute?displayProperty=fullName> attributo. Quando viene serializzato il tipo, un <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> eccezione viene generata se un tipo contiene un campo di istanza di un tipo che non è serializzabile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, si applicano le <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo sul campo che non è serializzabile.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare solo un avviso da questa regola se un <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo viene dichiarato che consente alle istanze del campo da serializzare e deserializzare.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che soddisfa la regola.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)



