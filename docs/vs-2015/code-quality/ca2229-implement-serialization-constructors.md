---
title: 'CA2229: Implementare costruttori di serializzazione | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 41e296a979557a42a96c2f57ce49610d88b98a40
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073164"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementare costruttori di serializzazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaccia, non è un delegato o l'interfaccia e viene soddisfatta una delle condizioni seguenti:

- Il tipo non dispone di un costruttore che accetta un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> oggetto e un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> oggetto (la firma del costruttore di serializzazione).

- Il tipo è non bloccato e il modificatore di accesso per il relativo costruttore di serializzazione non è protetta (famiglia).

- Il tipo è sealed e il modificatore di accesso per il relativo costruttore di serializzazione non è privato.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola è rilevante per i tipi che supportano la serializzazione personalizzata. Un tipo supporta la serializzazione personalizzata se implementa il <xref:System.Runtime.Serialization.ISerializable> interfaccia. È necessario il costruttore di serializzazione per deserializzare, o ricreare gli oggetti che sono stati serializzati utilizzando la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> (metodo).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il costruttore di serializzazione. Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare una violazione della regola. Il tipo non è deserializzabile e non funzionerà in molti scenari.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che soddisfa la regola.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
