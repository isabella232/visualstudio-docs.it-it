---
title: 'CA2236: chiamare metodi della classe base su tipi ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666701"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Chiamare metodi della classe base su tipi ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo deriva da un tipo che implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e viene soddisfatta una delle condizioni seguenti:

- Il tipo implementa il costruttore di serializzazione, ovvero un costruttore con la firma del parametro <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, ma non chiama il costruttore di serializzazione del tipo di base.

- Il tipo implementa il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ma non chiama il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> del tipo di base.

## <a name="rule-description"></a>Descrizione della regola
 In un processo di serializzazione personalizzato, un tipo implementa il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> per serializzare i campi e il costruttore di serializzazione per deserializzare i campi. Se il tipo deriva da un tipo che implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable>, il tipo di base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> il metodo e il costruttore di serializzazione devono essere chiamati per serializzare/deserializzare i campi del tipo di base. In caso contrario, il tipo non verrà serializzato e deserializzato correttamente. Si noti che se il tipo derivato non aggiunge nuovi campi, non è necessario che il tipo implementi il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> né il costruttore di serializzazione né chiami gli equivalenti del tipo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare il tipo di base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo o il costruttore di serializzazione dal costruttore o dal metodo di tipo derivato corrispondente.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo derivato che soddisfa la regola chiamando il costruttore di serializzazione e il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> della classe di base.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)
