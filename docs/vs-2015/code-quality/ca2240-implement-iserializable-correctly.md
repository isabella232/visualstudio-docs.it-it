---
title: 'CA2240: implementare ISerializable correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543663"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementare ISerializable in modo corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente è assegnabile all' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e viene soddisfatta una delle condizioni seguenti:

- Il tipo eredita ma non esegue l'override del <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodo e il tipo dichiara i campi di istanza che non sono contrassegnati con l' <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo.

- Il tipo non è sealed e il tipo implementa un <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo non visibile esternamente e sottoponibile a override.

## <a name="rule-description"></a>Descrizione della regola
 I campi di istanza dichiarati in un tipo che eredita l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia non vengono inclusi automaticamente nel processo di serializzazione. Per includere i campi, il tipo deve implementare il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo e il costruttore di serializzazione. Se i campi non devono essere serializzati, applicare l' <xref:System.NonSerializedAttribute> attributo ai campi per indicare in modo esplicito la decisione.

 Nei tipi non sealed, le implementazioni del <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo devono essere visibili esternamente. Pertanto, il metodo può essere chiamato da tipi derivati ed è sottoponibile a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> visibile e sottoponibile a override il metodo e verificare che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati in modo esplicito con l' <xref:System.NonSerializedAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due tipi serializzabili che violano la regola.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono risolte le due violazioni precedenti fornendo un'implementazione di [ISerializable. GetObjectData] sostituibile (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) nella classe Book e specificando un'implementazione di <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> sulla classe della libreria.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)
