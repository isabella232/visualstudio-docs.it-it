---
title: 'CA2002: Non bloccare oggetti con identità debole'
ms.date: 01/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ddeb32032f7fbd6ff088980c342405261e5b473
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548465"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Non bloccare oggetti con identità debole

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un thread tenta di acquisire un blocco su un oggetto con identità debole.

## <a name="rule-description"></a>Descrizione della regola

Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.

I seguenti tipi presentano un'identità debole e sono contrassegnati dalla regola:

- <xref:System.String>

- Le matrici di tipi valore, inclusi [i tipi integrali](/dotnet/csharp/language-reference/keywords/integral-types-table), [tipi a virgola mobile](/dotnet/csharp/language-reference/keywords/floating-point-types-table), e <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare un oggetto da un tipo che non è presente nell'elenco nella sezione Descrizione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate

[CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Esempio

L'esempio seguente illustra alcuni blocchi di oggetti che violano la regola.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Threading.Monitor>
- <xref:System.AppDomain>
- [blocco di istruzione (c#)](/dotnet/csharp/language-reference/keywords/lock-statement)
- [Istruzione SyncLock (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)