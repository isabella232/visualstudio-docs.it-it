---
title: 'CA2226: Gli operatori devono avere overload simmetrici'
ms.date: 03/11/2019
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
ms.openlocfilehash: 9d9e486d4193645335189c475fdd3ca220374d96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231432"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Gli operatori devono avere overload simmetrici

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un tipo implementa l'operatore di uguaglianza o di disuguaglianza e non implementa l'operatore opposto.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Non esistono circostanze in cui l'uguaglianza o la disuguaglianza è applicabile alle istanze di un tipo e l'operatore opposto non è definito. I tipi implementano in genere l'operatore di disuguaglianza restituendo il valore negato dell'operatore di uguaglianza.

Il C# compilatore genera un errore per le violazioni di questa regola.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, implementare gli operatori di uguaglianza e disuguaglianza oppure rimuovere quello presente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola. In tal caso, il tipo non funzionerà in modo coerente con .NET.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca2226.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (utilizzo). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

- [CA1046: Non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Gli overload degli operatori hanno alternative denominate](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224: Esegue l'override di Equals in un operatore di overload uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Eseguire l'override di GetHashCode sull'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)