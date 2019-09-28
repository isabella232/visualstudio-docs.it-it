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
dev_langs:
- CSharp
ms.openlocfilehash: b4db3074d334fe32f95c4d1b8446921c4e4d47ba
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481766"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Gli overload degli operatori hanno alternative con nome

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

È stato rilevato un overload dell'operatore e il metodo alternativo denominato previsto non è stato trovato.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

L'overload degli operatori consente di usare i simboli per rappresentare i calcoli per un tipo. Ad esempio, un tipo che sovraccarica il simbolo più `+` per l'aggiunta in genere avrà un membro alternativo denominato `Add`. Il membro alternativo denominato fornisce l'accesso alla stessa funzionalità dell'operatore. Viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.

Questa regola esamina:

- Operatori di cast impliciti ed espliciti in un tipo verificando la presenza di metodi denominati `To<typename>` e `From<typename>`.

- Gli operatori elencati nella tabella seguente:

|C#|Visual Basic|C++|Nome metodo alternativo|
|-|-|-|-|
|+ (binario)|+|+ (binario)|Aggiunta|
|+=|+=|+=|Aggiunta|
|&|e|&|BitwiseAnd|
|&=|E =|&=|BitwiseAnd|
|&#124;|Oppure|&#124;|BitwiseOr|
|&#124;=|Or=|&#124;=|BitwiseOr|
|--|N/D|--|Operatore di conversione|
|/|/|/|Dividi|
|/=|/=|/=|Dividi|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|CompareTo o compare|
|>=|>=|>=|CompareTo o compare|
|++|N/D|++|Operatore di incremento|
|!=|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|CompareTo o compare|
|<=|<=|\<=|CompareTo o compare|
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
|false|IsFalse|False|IsTrue (proprietà)|

\* N/r indica che non è possibile eseguire l'overload dell'operatore nella lingua selezionata.

> [!NOTE]
> In C#, quando un operatore binario viene sottoposto a overload, anche l'eventuale operatore di assegnazione corrispondente viene sottoposto a overload implicito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, implementare il metodo alternativo per l'operatore. Denominarlo utilizzando il nome alternativo consigliato.

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