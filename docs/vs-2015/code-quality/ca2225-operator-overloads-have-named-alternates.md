---
title: 'CA2225: Overload degli operatori hanno alternative con nome | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa90a1e97b563ef549cb3f628fcf9130a364c50a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967957"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Gli overload degli operatori hanno alternative con nome
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato.

## <a name="rule-description"></a>Descrizione della regola
 L'overload degli operatori consente di usare i simboli per rappresentare i calcoli per un tipo. Ad esempio, un tipo che esegue l'overload sul simbolo più (+) per l'aggiunta in genere necessario un membro alternativo denominato 'Add'. Il membro alternativo denominato fornisce l'accesso per la stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano gli operatori di overload.

 Questa regola esamina gli operatori elencati nella tabella seguente.

|C#|Visual Basic|C++|Nome alternativo|
|---------|------------------|-----------|--------------------|
|+ (binario)|+|+ (binario)|Aggiunta|
|+=|+=|+=|Aggiunta|
|&|e|&|BitwiseAnd|
|&=|And=|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|Or=|&#124;=|BitwiseOr|
|--|N/D|--|Operatore di conversione|
|/|/|/|Dividi|
|/=|/=|/=|Dividi|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|Compare|
|>=|>=|>=|Compare|
|++|N/D|++|Operatore di incremento|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Compare|
|<=|<=|\<=|Compare|
|&&|N/D|&&|LogicalAnd|
|&#124;&#124;|N/D|&#124;&#124;|LogicalOr|
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
|-(unario)|N/D|-|negate)|
|+ (unario)|N/D|+|Plus|
|False|IsFalse|False|IsTrue (proprietà)|

 N/d = = non possono essere sottoposti a overload nella lingua selezionata.

 La regola controlla anche gli operatori di cast impliciti ed espliciti in un tipo (`SomeType`) tramite il controllo dei metodi denominati `ToSomeType` e `FromSomeType`.

 In C#, quando viene eseguito l'overload di un operatore binario, l'operatore di assegnazione corrispondente, se presente, viene anche in modo implicito l'overload.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare il metodo alternativo per l'operatore. il nome usando il nome alternativo consigliato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola se si implementa una libreria condivisa. Le applicazioni possono ignorare un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente definisce una struttura che violano questa regola. Per correggere l'esempio, aggiungere un pubblico `Add(int x, int y)` metodo alla struttura.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore di uguaglianza sui tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Override di equals all'overload dell'operatore è uguale a](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
