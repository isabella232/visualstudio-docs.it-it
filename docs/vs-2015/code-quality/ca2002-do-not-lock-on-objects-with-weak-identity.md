---
title: 'CA2002: non bloccare su oggetti con identità vulnerabile | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 79f97de740ace9ccb59b13b3e4e30b34f38eb2f4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534667"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Non bloccare oggetti con identità debole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Category|Microsoft. affidabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un thread tenta di acquisire un blocco su un oggetto con un'identità vulnerabile.

## <a name="rule-description"></a>Descrizione della regola
 Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto. I tipi seguenti hanno un'identità debole e sono contrassegnati dalla regola:

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.String>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, utilizzare un oggetto di un tipo non presente nell'elenco della sezione Descrizione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="related-rules"></a>Regole correlate
 [CA2213: I campi eliminabili devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati alcuni blocchi di oggetti che violano la regola.

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 Istruzione [lock istruzione](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock](https://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)
