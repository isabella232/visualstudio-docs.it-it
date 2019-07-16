---
title: "CA1815: Override di equals e dell'operatore è uguale a sui tipi di valore | Microsoft Docs"
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e21585a7a56fde2fb46ea86adde92eecfd1a4565
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201688"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo valore pubblico non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName>, o non implementa l'operatore di uguaglianza (= =). Questa regola non verifica le enumerazioni.

## <a name="rule-description"></a>Descrizione della regola
 Per i tipi di valore, l'implementazione ereditata di <xref:System.Object.Equals%2A> Usa la libreria Reflection e confronta il contenuto di tutti i campi. La libreria Reflection è onerosa dal punto di vista del calcolo, inoltre il confronto di ogni campo per determinarne l'uguaglianza potrebbe essere superfluo. Se si prevede che gli utenti per confrontare o ordinare le istanze oppure le utilizzino come chiavi di tabelle hash, il tipo di valore deve implementare <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione in uso supporta l'overload degli operatori, è necessario specificare anche un'implementazione degli operatori di uguaglianza e disuguaglianza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, fornire un'implementazione di <xref:System.Object.Equals%2A>. Se possibile, implementare l'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se le istanze del tipo di valore non verranno confrontate tra loro.

## <a name="example-of-a-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 Nell'esempio seguente illustra una struttura (tipo di valore) che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Esempio di procedura di correzione

### <a name="description"></a>DESCRIZIONE
 Nell'esempio seguente consente di correggere la violazione precedente eseguendo l'override <xref:System.ValueType.Equals%2A?displayProperty=fullName> e l'implementazione degli operatori di uguaglianza (= =,! =).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA2224: Override di equals all'overload dell'operatore è uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Object.Equals%2A?displayProperty=fullName>
