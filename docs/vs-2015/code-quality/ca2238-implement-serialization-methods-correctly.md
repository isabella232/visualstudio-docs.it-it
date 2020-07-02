---
title: 'CA2238: implementare correttamente i metodi di serializzazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 98e825fd5543b928569b99218c9054aff666e0fe
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545145"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementare correttamente i metodi di serializzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [CA2238: implementare correttamente i metodi di serializzazione](/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).

|Elemento|valore|
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Category|Microsoft. Usage|
|Modifica importante|Interruzioni: se il metodo è visibile all'esterno dell'assembly.<br /><br /> Senza interruzioni: se il metodo non è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Un metodo che gestisce un evento di serializzazione non dispone della visibilità, del tipo restituito o della firma corretta.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo viene designato come gestore eventi di serializzazione applicando uno degli attributi dell'evento di serializzazione seguenti:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  I gestori eventi di serializzazione accettano un solo parametro di tipo <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> , restituiscono `void` e hanno `private` visibilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere la firma, il tipo restituito o la visibilità del gestore eventi di serializzazione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati i gestori eventi di serializzazione dichiarati correttamente.

 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)
