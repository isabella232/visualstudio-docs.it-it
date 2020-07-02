---
title: 'CA2229: implementare costruttori di serializzazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba654496d80654f0d9790a01bbc41326f7a5f13e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540491"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementare costruttori di serializzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il tipo implementa l' <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia, non è un delegato o un'interfaccia e viene soddisfatta una delle condizioni seguenti:

- Il tipo non dispone di un costruttore che accetta un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> oggetto e un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> oggetto (la firma del costruttore di serializzazione).

- Il tipo è non sealed e il modificatore di accesso per il costruttore di serializzazione non è protetto (famiglia).

- Il tipo è sealed e il modificatore di accesso per il relativo costruttore di serializzazione non è privato.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola è pertinente per i tipi che supportano la serializzazione personalizzata. Un tipo supporta la serializzazione personalizzata se implementa l' <xref:System.Runtime.Serialization.ISerializable> interfaccia. Il costruttore di serializzazione è necessario per deserializzare o ricreare oggetti serializzati tramite il <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare una violazione della regola. Il tipo non sarà deserializzabile e non funzionerà in molti scenari.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che soddisfa la regola.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
