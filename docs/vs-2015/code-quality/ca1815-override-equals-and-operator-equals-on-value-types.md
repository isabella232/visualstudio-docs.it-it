---
title: "CA1815: eseguire l'override di Equals e operator uguale ai tipi di valore | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc5dc311fd85af2b6a0eb3e29e9932614ca55193
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543910"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo di valore pubblico non esegue l'override di <xref:System.Object.Equals%2A?displayProperty=fullName> o non implementa l'operatore di uguaglianza (= =). Questa regola non controlla le enumerazioni.

## <a name="rule-description"></a>Descrizione della regola
 Per i tipi di valore, l'implementazione ereditata di <xref:System.Object.Equals%2A> Usa la libreria di reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti confrontino o ordinino le istanze o le usino come chiavi della tabella hash, il tipo di valore deve implementare <xref:System.Object.Equals%2A> . Se il linguaggio di programmazione in uso supporta l'overload degli operatori, è necessario specificare anche un'implementazione degli operatori di uguaglianza e disuguaglianza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.Equals%2A> . Se possibile, implementare l'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se le istanze del tipo di valore non verranno confrontate tra loro.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrata una struttura (tipo di valore) che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Esempio di correzione

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene corretta la violazione precedente eseguendo <xref:System.ValueType.Equals%2A?displayProperty=fullName> l'override e implementando gli operatori di uguaglianza (= =,! =).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2224: Eseguire l'override di Equals all'overload dell'operatore "uguale a"](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Object.Equals%2A?displayProperty=fullName>
