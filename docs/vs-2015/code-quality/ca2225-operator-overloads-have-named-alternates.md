---
title: 'CA2225: gli overload degli operatori hanno alternative denominate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545223"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Gli overload degli operatori hanno alternative con nome
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato.

## <a name="rule-description"></a>Descrizione della regola
 L'overload degli operatori consente di usare i simboli per rappresentare i calcoli per un tipo. Ad esempio, un tipo che sovraccarica il segno più (+) per l'aggiunta in genere avrà un membro alternativo denominato "Add". Il membro alternativo denominato fornisce l'accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.

 Questa regola esamina gli operatori elencati nella tabella seguente.

|C#|Visual Basic|C++|Nome alternativo|
|---------|------------------|-----------|--------------------|
|+ (binario)|+|+ (binario)|Aggiunta|
|+=|+=|+=|Aggiunta|
|&|e|&|BitwiseAnd|
|&=|E =|&=|BitwiseAnd|
|&#124;|Oppure|&#124;|BitwiseOr|
|&#124;=|O =|&#124;=|BitwiseOr|
|--|N/D|--|Operatore di conversione|
|/|/|/|Divisione|
|/=|/=|/=|Divisione|
|==|=|==|Uguale a|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Confronto|
|>=|>=|>=|Confronto|
|++|N/D|++|Incremento valore Identity|
|<>|!=|Uguale a|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Confronto|
|<=|<=|\<=|Confronto|
|&&|N/D|&&|LogicalAnd|
|&#124;&#124;|N/D|&#124;&#124;|Operatore logico|
|!|N/D|!|LogicalNot|
|%|Mod|%|Mod o resto|
|%=|N/D|%=|Mod|
|* (binario)|*|*|Moltiplicazione|
|*=|N/D|*=|Moltiplicazione|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|N/D|>>=|RightShift|
|-(binario)|-(binario)|-(binario)|Sottrazione|
|-=|N/D|-=|Sottrazione|
|true|IsTrue|N/D|IsTrue (proprietà)|
| - (unario)   |N/D|-|Negate|
|+ (unario)|N/D|+|Plus|
|false|IsFalse|False|IsTrue (proprietà)|

 Non è possibile eseguire l'overload di N/A = = nella lingua selezionata.

 La regola controlla anche gli operatori cast impliciti ed espliciti in un tipo ( `SomeType` ) controllando la presenza di metodi denominati `ToSomeType` e `FromSomeType` .

 In C#, quando un operatore binario viene sottoposto a overload, anche l'eventuale operatore di assegnazione corrispondente viene sottoposto a overload implicito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il metodo alternativo per l'operatore; denominarlo utilizzando il nome alternativo consigliato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola se si sta implementando una libreria condivisa. Le applicazioni possono ignorare un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene definita una struttura che viola questa regola. Per correggere l'esempio, aggiungere un `Add(int x, int y)` Metodo pubblico alla struttura.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eseguire l'override di Equals all'overload dell'operatore "uguale a"](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
