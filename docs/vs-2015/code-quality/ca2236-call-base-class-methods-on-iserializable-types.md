---
title: 'CA2236: Chiamare metodi della classe di base su tipi ISerializable | Microsoft Docs'
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
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3087c3aa4b7d1e1fcba43dafbdf717cfd33e10cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238576"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Chiamare metodi della classe base su tipi ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo deriva da un tipo che implementa il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e una delle condizioni seguenti è true:

-   Il tipo implementa il costruttore di serializzazione, vale a dire, un costruttore con la <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> firma di parametro, ma non chiama il costruttore di serializzazione del tipo di base.

-   Il tipo implementa la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (metodo), ma non chiama il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo del tipo di base.

## <a name="rule-description"></a>Descrizione della regola
 In un processo di serializzazione personalizzata, un tipo implementa la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo per serializzare i relativi campi e il costruttore di serializzazione per deserializzare i campi. Se il tipo deriva da un tipo che implementa il <xref:System.Runtime.Serialization.ISerializable> dell'interfaccia, il tipo di base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> costruttore di serializzazione e metodo deve essere chiamato per serializzare o deserializzare i campi del tipo di base. In caso contrario, il tipo verrà non serializzato e deserializzato correttamente. Si noti che se il tipo derivato non aggiunge i nuovi campi, il tipo non necessario implementare il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo né il costruttore di serializzazione o chiamare gli equivalenti del tipo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, chiamare il tipo di base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> costruttore di serializzazione o il metodo dal corrispondente derivato metodo con tipo o il costruttore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo derivato che soddisfa la regola chiamando il costruttore di serializzazione e <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo della classe di base.

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



