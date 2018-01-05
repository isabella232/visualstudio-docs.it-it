---
title: "CA2002: Non bloccare oggetti con identità debole | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 55bc495f116b4a7be8c118b47c71a9fed9f85777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
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
 Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione. Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto. I tipi seguenti presentano un'identità debole e sono contrassegnati dalla regola:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, utilizzare un oggetto da un tipo che non è presente nell'elenco nella sezione Descrizione.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra alcuni blocchi di oggetti che violano la regola.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [Istruzione lock](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [Istruzione SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)