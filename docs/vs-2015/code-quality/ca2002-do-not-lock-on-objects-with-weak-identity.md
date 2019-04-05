---
title: 'CA2002: Non bloccare oggetti con identità debole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9c525aa18e94e7951e6355c959a105aa5841e10d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955377"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Non bloccare oggetti con identità debole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un thread tenta di acquisire un blocco su un oggetto con identità debole.

## <a name="rule-description"></a>Descrizione della regola
 Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto. I seguenti tipi presentano un'identità debole e sono contrassegnati dalla regola:

-   <xref:System.MarshalByRefObject>

-   <xref:System.ExecutionEngineException>

-   <xref:System.OutOfMemoryException>

-   <xref:System.StackOverflowException>

-   <xref:System.String>

-   <xref:System.Reflection.MemberInfo>

-   <xref:System.Reflection.ParameterInfo>

-   <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, usare un oggetto da un tipo che non è presente nell'elenco nella sezione Descrizione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Esempio
 L'esempio seguente illustra alcuni blocchi di oggetti che violano la regola.

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [Istruzione lock](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [istruzione SyncLock](http://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)
