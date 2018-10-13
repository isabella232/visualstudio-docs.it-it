---
title: 'CA2107: Controllare negare e consentire solo utilizzo | Microsoft Docs'
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
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b317ddb69dea8241ead6bb70d50c3b99d96bd078
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178646"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Controllare l'utilizzo di Deny e PermitOnly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene un controllo di sicurezza che specifica l'azione di sicurezza Deny o PermitOnly.

## <a name="rule-description"></a>Descrizione della regola
 Il [utilizzando il metodo PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649) e <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> azioni di sicurezza devono essere utilizzate solo da coloro che hanno una conoscenza approfondita di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] sicurezza. Il codice che usa queste azioni di sicurezza deve essere sottoposto a una revisione della sicurezza.

 Nega modifica il comportamento predefinito dell'analisi dello stack che si verifica in risposta a una richiesta di sicurezza. Consente di specificare le autorizzazioni che non devono essere concesse per la durata del metodo Deny, indipendentemente dalle autorizzazioni effettive dei chiamanti nello stack di chiamate. Se il percorso stack rileva un metodo protetto da Nega e l'autorizzazione richiesta è inclusa nelle autorizzazioni negate, il percorso stack avrà esito negativo. PermitOnly modifica anche il comportamento predefinito dell'analisi dello stack. Consente al codice specificare solo le autorizzazioni che possono essere concesse, indipendentemente dalle autorizzazioni dei chiamanti. Se il percorso stack viene rilevato un metodo che è protetta da PermitOnly e se l'autorizzazione richiesta non è incluso nelle autorizzazioni specificate da PermitOnly, analisi dello stack ha esito negativo.

 Il codice che si basa su queste azioni deve essere valutato attentamente per le vulnerabilità di sicurezza grazie a utilità limitata e comportamento meno evidente. Si consideri quanto segue.

-   [Le richieste di collegamento](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) non sono interessati da Deny o PermitOnly.

-   In caso di Deny o PermitOnly nello stesso stack frame della richiesta che fa sì che il percorso dello stack, le azioni di sicurezza non hanno alcun effetto.

-   In genere possano specificare i valori che vengono usati per costruire le autorizzazioni in base al percorso in diversi modi. Negando l'accesso a una forma di percorso non negare l'accesso a tutti i form. Se, ad esempio, una condivisione file \\\Server\Share è mappata a un'unità di rete x:, per negare l'accesso a un file nella condivisione, è necessario negare \\\Server\Share\File, X:\File e ogni altro percorso che accede al file.

-   Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> può terminare un'analisi dello stack prima che venga raggiunto Deny o PermitOnly.

-   Se un'istruzione Deny ha alcun effetto, vale a dire, quando un chiamante ha un'autorizzazione che è bloccata da Deny, il chiamante può accedere alla risorsa protetta direttamente, ignorando l'istruzione Deny. Analogamente, se il chiamante non ha l'autorizzazione negata, analisi dello stack avrà esito negativo senza l'istruzione Deny.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Qualsiasi utilizzo di queste azioni di sicurezza comporta una violazione. Per correggere una violazione, non utilizzare queste azioni di sicurezza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo dopo aver completato un'analisi della sicurezza.

## <a name="example"></a>Esempio
 L'esempio seguente illustra alcune limitazioni di negazione.

 La libreria seguente contiene una classe che dispone di due metodi che sono identici a eccezione dei requisiti di sicurezza da abilitare la protezione.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione seguente illustra gli effetti di negazione sui metodi protetti dalla libreria.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 Questo esempio produce il seguente output:

 **Domanda: Negazione del chiamante non ha effetto su richiesta con autorizzazione oggetto dell'asserzione. ** 
 **LinkDemand: negazione del chiamante non ha alcun effetto su LinkDemand con autorizzazione oggetto dell'asserzione.** 
 **LinkDemand: negazione del chiamante non ha alcun effetto con il codice protetto da LinkDemand.** 
 **LinkDemand: negare questa non ha alcun effetto con il codice protetto da LinkDemand.**
## <a name="see-also"></a>Vedere anche
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [eseguendo l'override dei controlli di sicurezza](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [mediante il metodo PermitOnly](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)



