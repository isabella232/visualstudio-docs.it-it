---
title: 'CA2225: Gli overload degli operatori hanno alternative con nome'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f427bcdf4ec4e88dcc2842699d738dae7e8e09d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546911"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Gli overload degli operatori hanno alternative con nome

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

È stato rilevato un overload dell'operatore e il metodo alternativo denominato previsto non è stato trovato.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

L'overload degli operatori consente di usare i simboli per rappresentare i calcoli per un tipo. Ad esempio, un tipo che sovraccarica il segno più (+) per l'aggiunta in genere avrà un membro alternativo denominato "Add". Il membro alternativo denominato fornisce l'accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.

Questa regola esamina gli operatori elencati nella tabella seguente.

|C#|Visual Basic|C++|Nome alternativo|
|---------|------------------|-----------|--------------------|
|+ (binario)|+|+ (binario)|Aggiunta|
|+=|+=|+=|Aggiunta|
|&|e|&|BitwiseAnd|
|&=|E =|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|Or=|&#124;=|BitwiseOr|
|--|N/D|--|Operatore di conversione|
|/|/|/|Dividi|
|/=|/=|/=|Dividi|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Compare|
|>=|>=|>=|Compare|
|++|N/D|++|Operatore di incremento|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Compare|
|<=|<=|\<=|Compare|
|&&|N/D|&&|LogicalAnd|
|&#124;&#124;|N/D|&#124;&#124;|Operatore logico|
|!|N/D|!|LogicalNot|
|%|Mod|%|Mod o resto|
|%=|N/D|%=|Mod|
|* (binario)|*|*|Multiply|
|*=|N/D|*=|Multiply|
|~|not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|N/D|>>=|RightShift|
|-(binario)|-(binario)|-(binario)|Sottrai|
|-=|N/D|-=|Sottrai|
|true|IsTrue|N/D|IsTrue (proprietà)|
|-(unario)|N/D|-|Negare|
|+ (unario)|N/D|+|Più|
|False|IsFalse|False|IsTrue (proprietà)|

Non è possibile eseguire l'overload di N/A = = nella lingua selezionata.

La regola controlla anche gli operatori cast impliciti ed espliciti in`SomeType`un tipo () controllando `ToSomeType` la `FromSomeType`presenza di metodi denominati e.

In C#, quando un operatore binario viene sottoposto a overload, anche l'eventuale operatore di assegnazione corrispondente viene sottoposto a overload implicito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, implementare il metodo alternativo per l'operatore; denominarlo utilizzando il nome alternativo consigliato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non eliminare un avviso da questa regola se si sta implementando una libreria condivisa. Le applicazioni possono ignorare un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (utilizzo). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene definita una struttura che viola questa regola. Per correggere l'esempio, aggiungere un metodo `Add(int x, int y)` pubblico alla struttura.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1046: Non eseguire l'overload dell'operatore uguale ai tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Gli operatori devono avere Overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Esegue l'override di Equals in un operatore di overload uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Eseguire l'override di GetHashCode sull'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)