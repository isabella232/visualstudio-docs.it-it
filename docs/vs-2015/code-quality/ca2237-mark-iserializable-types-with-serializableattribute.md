---
title: 'CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f9d75a75449a07a5e9f651be0ba61598a29674ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201530"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Implementa un tipo visibile esternamente il <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia e il tipo non è contrassegnato con il <xref:System.SerializableAttribute?displayProperty=fullName> attributo. La regola ignora i tipi derivati non può essere serializzato il cui tipo di base.

## <a name="rule-description"></a>Descrizione della regola
 Per essere riconosciuti da common language runtime come serializzabile, i tipi devono essere contrassegnati con il <xref:System.SerializableAttribute> attributo anche se il tipo Usa una routine di serializzazione personalizzata tramite l'implementazione del <xref:System.Runtime.Serialization.ISerializable> interfaccia.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, si applicano le <xref:System.SerializableAttribute> al tipo di attributo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola per le classi di eccezione in quanto devono essere serializzabili per funzionare correttamente in diversi domini applicazione.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Rimuovere il commento di <xref:System.SerializableAttribute> riga per soddisfare la regola dell'attributo.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2236: Chiamare metodi della classe di base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)
