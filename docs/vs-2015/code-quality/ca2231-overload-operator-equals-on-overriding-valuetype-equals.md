---
title: "CA2231: Operatore di Overload di equals all'override di ValueType. Equals | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ebbe414c26d5784f8db96125c4112c01ca82eecb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829760"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Esegue l'override di un tipo di valore <xref:System.Object.Equals%2A?displayProperty=fullName> ma non implementa l'operatore di uguaglianza.

## <a name="rule-description"></a>Descrizione della regola
 Nella maggior parte dei linguaggi di programmazione vi è Nessuna implementazione predefinita dell'operatore di uguaglianza (= =) per i tipi di valore. Se il linguaggio di programmazione supporta l'overload dell'operatore, è consigliabile implementare l'operatore di uguaglianza. Deve essere identico a quello del relativo comportamento <xref:System.Object.Equals%2A>.

 È possibile usare l'operatore di uguaglianza predefinito in un'implementazione di overload dell'operatore di uguaglianza. Questa operazione causerà un overflow dello stack. Per implementare l'operatore di uguaglianza, usare il metodo di Object. Equals nell'implementazione. Ad esempio:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, implementare l'operatore di uguaglianza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, è consigliabile fornire l'operatore di uguaglianza se possibile.

## <a name="example"></a>Esempio
 L'esempio seguente definisce un tipo che viola questa regola.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EqualsGetHashCode/cs/FxCop.Usage.EqualsGetHashCode.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Gli overload degli operatori hanno alternative con nome](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Object.Equals%2A?displayProperty=fullName>



