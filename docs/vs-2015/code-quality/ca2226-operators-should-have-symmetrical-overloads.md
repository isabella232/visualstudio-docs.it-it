---
title: 'CA2226: Gli operatori devono avere overload simmetrici | Microsoft Docs'
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
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6df4a36dae04dadf61790e7be16834dc0d59bdc0
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589084"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Gli operatori devono avere overload simmetrici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2226: gli operatori devono avere overload simmetrici](https://docs.microsoft.com/visualstudio/code-quality/ca2226-operators-should-have-symmetrical-overloads).

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Il tipo non funzionerà in modo che sia coerenza con il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



