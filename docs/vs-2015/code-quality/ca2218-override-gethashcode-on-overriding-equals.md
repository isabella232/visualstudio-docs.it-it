---
title: "CA2218: Eseguire l'Override di GetHashCode all'override di Equals | Microsoft Docs"
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
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc9e72639e123e0a99c4423b460bc4122995971c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881911"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Eseguire l'override di GetHashCode all'override di Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Esegue l'override di un tipo pubblico <xref:System.Object.Equals%2A?displayProperty=fullName> ma non esegue l'override <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Object.GetHashCode%2A> Restituisce un valore, in base all'istanza corrente, adatto per algoritmi hash e strutture di dati, ad esempio una tabella hash. Due oggetti sono dello stesso tipo e uguali devono restituire lo stesso codice hash per garantire il corretto funzionano delle istanze dei tipi seguenti:

-   <xref:System.Collections.Hashtable?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

-   Tipi che implementano <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.GetHashCode%2A>. Per una coppia di oggetti dello stesso tipo, è necessario assicurarsi che l'implementazione restituisce lo stesso valore se l'implementazione di <xref:System.Object.Equals%2A> restituisce `true` per la coppia.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="class-example"></a>Esempio di classe

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una classe (tipo riferimento) che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>Commenti
 Nell'esempio seguente la violazione viene corretta eseguendo l'override <xref:System.Object.GetHashCode>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>Esempio di struttura

### <a name="description"></a>Descrizione
 Nell'esempio seguente illustra una struttura (tipo di valore) che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>Commenti
 Nell'esempio seguente la violazione viene corretta eseguendo l'override <xref:System.Object.GetHashCode>.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operatori di uguaglianza](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)