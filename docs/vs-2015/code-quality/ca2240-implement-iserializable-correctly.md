---
title: 'CA2240: Implementare ISerializable in modo corretto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 08c383f42e7667a3f822298c14f29e81d22a309b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589654"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementare ISerializable in modo corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2240: implementare ISerializable in modo corretto](https://docs.microsoft.com/visualstudio/code-quality/ca2240-implement-iserializable-correctly).

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente è assegnabile al <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e una delle condizioni seguenti è true:

-   Il tipo eredita, ma non esegue l'override di <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodo e il tipo dichiara i campi di istanza che non siano contrassegnati con il <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo.

-   Il tipo non è bloccato e il tipo implementa un <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo che non è visibile esternamente e sottoponibile a override.

## <a name="rule-description"></a>Descrizione della regola
 Istanza i campi che vengono dichiarati in un tipo che eredita il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia non sono inclusi automaticamente nel processo di serializzazione. Per includere i campi, il tipo deve implementare il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo e il costruttore di serializzazione. Se i campi non devono essere serializzati, applicare il <xref:System.NonSerializedAttribute> i campi per indicare in modo esplicito la decisione dell'attributo.

 Nei tipi non sealed, le implementazioni del <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo deve essere visibile esternamente. Pertanto, il metodo può essere chiamato da tipi derivati e sottoponibile a override.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, verificare i <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodo visibile e sottoponibile a override e accertarsi che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati in modo esplicito con la <xref:System.NonSerializedAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra due tipi serializzabili che violano la regola.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente corregge le violazioni precedente due fornendo un'implementazione sottoponibile a override di [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) nella classe Book e fornendo un'implementazione di <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> nella classe di libreria.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)



