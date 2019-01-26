---
title: 'CA2226: Gli operatori devono avere overload simmetrici'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6a38f6f4e76f5195e042b0ede2b2a8a5384a1cf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938016"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Gli operatori devono avere overload simmetrici

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo implementa l'operatore di uguaglianza o di disuguaglianza e non implementa l'operatore opposto.

## <a name="rule-description"></a>Descrizione della regola
 Non esistono nessuna circostanza in cui è applicabile alle istanze di un tipo di uguaglianza o disuguaglianza e non è definito l'operatore opposto. Tipi implementano in genere l'operatore di disuguaglianza, restituendo il valore negato dell'operatore di uguaglianza.

 Il compilatore c# genera un errore per le violazioni di questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare l'uguaglianza e gli operatori di disuguaglianza o rimuovere quello che è presente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. Il tipo non funzionerà in modo che sia coerenza con .NET Framework.

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore di uguaglianza sui tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Override di equals all'overload dell'operatore è uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)