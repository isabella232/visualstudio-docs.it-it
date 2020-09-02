---
title: "CA2224: esegue l'override di Equals per l'overload dell'operatore Equals | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 39272790b6ef366c64d45e0aea238606d0b62bf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538636"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Eseguire l'override di Equals all'overload dell'operatore "uguale a"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo pubblico implementa l'operatore di uguaglianza, ma non esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Descrizione della regola
 L'operatore di uguaglianza è concepito come un modo sintatticamente pratico per accedere alla funzionalità del <xref:System.Object.Equals%2A> metodo. Se si implementa l'operatore di uguaglianza, la relativa logica deve essere identica a quella di <xref:System.Object.Equals%2A> .

 Il compilatore C# genera un avviso se il codice viola questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, è necessario rimuovere l'implementazione dell'operatore di uguaglianza oppure eseguire l'override di e fare in modo che <xref:System.Object.Equals%2A> i due metodi restituiscano gli stessi valori. Se l'operatore di uguaglianza non introduce un comportamento incoerente, è possibile correggere la violazione fornendo un'implementazione di <xref:System.Object.Equals%2A> che chiama il <xref:System.Object.Equals%2A> metodo nella classe di base.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se l'operatore di uguaglianza restituisce lo stesso valore dell'implementazione ereditata di <xref:System.Object.Equals%2A> . La sezione di esempio include un tipo che potrebbe eliminare in modo sicuro un avviso da questa regola.

## <a name="examples-of-inconsistent-equality-definitions"></a>Esempi di definizioni di uguaglianza incoerenti

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrato un tipo con definizioni incoerenti di uguaglianza. `BadPoint` modifica il significato di uguaglianza fornendo un'implementazione personalizzata dell'operatore di uguaglianza, ma non esegue l'override di in <xref:System.Object.Equals%2A> modo che si comportano in modo identico.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Esempio
 Il codice seguente verifica il comportamento di `BadPoint` .

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Questo esempio produce il seguente output:

 **a = ([0] 1, 1) e b = ([1] 2, 2) sono uguali? No** 
 **a = = b? Nessun** 
 **a1 e un sono uguali? Sì** 
 **a1 = = a? Sì** 
 **b e bcopy sono uguali? Nessun** 
 **b = = bcopy? Sì**
## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che tecnicamente viola questa regola, ma che non si comporta in modo incoerente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Esempio
 Il codice seguente verifica il comportamento di `GoodPoint` .

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Questo esempio produce il seguente output:

 **a = (1, 1) e b = (2, 2) sono uguali? No** 
 **a = = b? Nessun** 
 **a1 e un sono uguali? Sì** 
 **a1 = = a? Sì** 
 **b e bcopy sono uguali? Sì** 
 **b = = bcopy? Sì**
## <a name="class-example"></a>Esempio di classe

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una classe (tipo di riferimento) che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene corretta la violazione eseguendo l'override di <xref:System.Object.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Esempio di struttura

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una struttura (tipo di valore) che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene corretta la violazione eseguendo l'override di <xref:System.ValueType.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
