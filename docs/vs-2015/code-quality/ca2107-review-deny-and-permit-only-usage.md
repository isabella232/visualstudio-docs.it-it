---
title: "CA2107: verificare l'utilizzo di Deny e Consenti solo | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f273ea5f58babf7a0c04f6b0758732d43aab7db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547771"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Controllare l'uso di Deny e PermitOnly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene un controllo di sicurezza che specifica l'azione PermitOnly o nega sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 L' [utilizzo del metodo PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649) e delle <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> azioni di sicurezza deve essere utilizzato solo da coloro che hanno una conoscenza avanzata della [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sicurezza. Il codice che usa queste azioni di sicurezza deve essere sottoposto a una revisione della sicurezza.

 Deny modifica il comportamento predefinito del percorso stack che si verifica in risposta a una richiesta di sicurezza. Consente di specificare le autorizzazioni che non devono essere concesse per la durata del metodo di negazione, indipendentemente dalle autorizzazioni effettive dei chiamanti nello stack di chiamate. Se il percorso stack rileva un metodo protetto da Deny e se l'autorizzazione richiesta è inclusa nelle autorizzazioni negate, il percorso stack ha esito negativo. PermitOnly modifica anche il comportamento predefinito del percorso stack. Consente al codice di specificare solo le autorizzazioni che è possibile concedere, indipendentemente dalle autorizzazioni dei chiamanti. Se il percorso stack rileva un metodo protetto da PermitOnly e se l'autorizzazione richiesta non è inclusa nelle autorizzazioni specificate da PermitOnly, il percorso dello stack ha esito negativo.

 Il codice che si basa su queste azioni deve essere valutato attentamente per individuare le vulnerabilità di sicurezza a causa dell'utilità limitata e del comportamento sottile. Considerare quanto segue:

- Le [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) non sono interessate da Deny o PermitOnly.

- Se l'istruzione DENY o PermitOnly si verifica nello stesso stack frame della richiesta che causa il percorso dello stack, le azioni di sicurezza non hanno alcun effetto.

- I valori utilizzati per costruire autorizzazioni basate sul percorso possono in genere essere specificati in diversi modi. Negando l'accesso a un modulo del percorso non viene negato l'accesso a tutti i moduli. Se, ad esempio, \\ viene eseguito il mapping di una condivisione file \server\share a un'unità di rete X:, per negare l'accesso a un file nella condivisione, è necessario negare \\ \Server\Share\File, X:\File e ogni altro percorso che accede al file.

- Un oggetto <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> può terminare un percorso stack prima che venga raggiunto il valore Deny o PermitOnly.

- Se un'istruzione DENY ha un effetto, ovvero quando un chiamante dispone di un'autorizzazione bloccata dall'istruzione DENY, il chiamante può accedere direttamente alla risorsa protetta, ignorando la negazione. Analogamente, se il chiamante non dispone dell'autorizzazione negata, il percorso stack avrà esito negativo senza l'autorizzazione Deny.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Qualsiasi utilizzo di queste azioni di sicurezza provocherà una violazione. Per correggere una violazione, non usare queste azioni di sicurezza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo aver completato una verifica della sicurezza.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrate alcune limitazioni di Deny.

 La libreria seguente contiene una classe con due metodi identici, ad eccezione delle richieste di sicurezza che le proteggono.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Esempio
 Nell'applicazione seguente vengono illustrati gli effetti di Deny sui metodi protetti dalla libreria.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Questo esempio produce il seguente output:

 **Richiesta: la negazione del chiamante non ha effetto su richiesta con l'autorizzazione dichiarata.** 
 **LinkDemand: la negazione del chiamante non ha alcun effetto su LinkDemand con l'autorizzazione asserita.** 
 **LinkDemand: la negazione del chiamante non ha alcun effetto con il codice protetto da LinkDemand.** 
 **LinkDemand: questa negazione non ha alcun effetto con il codice protetto da LinkDemand.**
## <a name="see-also"></a>Vedere anche
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Linee guida per la codifica protetta](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [override dei controlli di sicurezza](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [tramite il metodo PermitOnly](https://msdn.microsoft.com/8c7bdb7f-882f-45b7-908c-6cbaa1767649)
