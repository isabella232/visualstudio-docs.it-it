---
title: 'CA2237: contrassegnare i tipi ISerializable con SerializableAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8778b0bfa035c782cf35d205fc59d463112196c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545158"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo visibile esternamente implementa l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e il tipo non è contrassegnato con l' <xref:System.SerializableAttribute?displayProperty=fullName> attributo. La regola ignora i tipi derivati il cui tipo di base non è serializzabile.

## <a name="rule-description"></a>Descrizione della regola
 Per essere riconosciuti dal Common Language Runtime come serializzabile, i tipi devono essere contrassegnati con l' <xref:System.SerializableAttribute> attributo anche se il tipo usa una routine di serializzazione personalizzata tramite l'implementazione dell' <xref:System.Runtime.Serialization.ISerializable> interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, applicare l' <xref:System.SerializableAttribute> attributo al tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola per le classi di eccezione perché devono essere serializzabili per funzionare correttamente tra domini dell'applicazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Rimuovere il commento dalla <xref:System.SerializableAttribute> riga dell'attributo per soddisfare la regola.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)
