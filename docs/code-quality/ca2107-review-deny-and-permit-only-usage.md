---
title: "CA2107: Controllare l'uso di Deny e PermitOnly"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c251b9fbf8327369acf20ef6acea0518e2b16913
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910287"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Controllare l'uso di Deny e PermitOnly

|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo contiene un controllo di sicurezza che specifica l'azione di sicurezza Deny o PermitOnly.

## <a name="rule-description"></a>Descrizione della regola
 Il <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> azione di sicurezza deve essere utilizzato solo da coloro che hanno una conoscenza approfondita della sicurezza di .NET Framework. Il codice che usa queste azioni di sicurezza deve essere sottoposto a una revisione della sicurezza.

 Nega modifica il comportamento predefinito dell'analisi dello stack che si verifica in risposta a una richiesta di sicurezza. Consente di specificare le autorizzazioni che non devono essere concesse per la durata del metodo Deny, indipendentemente dalle autorizzazioni effettive dei chiamanti nello stack di chiamate. Se il percorso stack rileva un metodo protetto da Nega e l'autorizzazione richiesta è inclusa nelle autorizzazioni negate, il percorso stack avrà esito negativo. PermitOnly modifica anche il comportamento predefinito dell'analisi dello stack. Consente al codice specificare solo le autorizzazioni che possono essere concesse, indipendentemente dalle autorizzazioni dei chiamanti. Se il percorso stack viene rilevato un metodo che è protetta da PermitOnly e se l'autorizzazione richiesta non è incluso nelle autorizzazioni specificate da PermitOnly, analisi dello stack ha esito negativo.

 Il codice che si basa su queste azioni deve essere valutato attentamente per le vulnerabilità di sicurezza grazie a utilità limitata e comportamento meno evidente. Si consideri quanto segue.

- [Le richieste di collegamento](/dotnet/framework/misc/link-demands) non sono interessati da Deny o PermitOnly.

- In caso di Deny o PermitOnly nello stesso stack frame della richiesta che fa sì che il percorso dello stack, le azioni di sicurezza non hanno alcun effetto.

- In genere possano specificare i valori che vengono usati per costruire le autorizzazioni in base al percorso in diversi modi. Negando l'accesso a una forma di percorso non negare l'accesso a tutti i form. Se, ad esempio, una condivisione file \\\Server\Share è mappata a un'unità di rete x:, per negare l'accesso a un file nella condivisione, è necessario negare \\\Server\Share\File X:\File e ogni altro percorso che accede al file.

- Un <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> può terminare un'analisi dello stack prima che venga raggiunto Deny o PermitOnly.

- Se un'istruzione Deny ha alcun effetto, vale a dire, quando un chiamante ha un'autorizzazione che è bloccata da Deny, il chiamante può accedere alla risorsa protetta direttamente, ignorando l'istruzione Deny. Analogamente, se il chiamante non ha l'autorizzazione negata, analisi dello stack avrà esito negativo senza l'istruzione Deny.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Qualsiasi utilizzo di queste azioni di sicurezza comporta una violazione. Per correggere una violazione, non utilizzare queste azioni di sicurezza.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Eliminare un avviso da questa regola solo dopo aver completato un'analisi della sicurezza.

## <a name="example-1"></a>Esempio 1
 L'esempio seguente illustra alcune limitazioni di negazione.

 La libreria seguente contiene una classe che dispone di due metodi che sono identici a eccezione dei requisiti di sicurezza da abilitare la protezione.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example-2"></a>Esempio 2
 L'applicazione seguente illustra gli effetti di negazione sui metodi protetti dalla libreria.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

Questo esempio produce il seguente output:

```txt
Demand: Caller's Deny has no effect on Demand with the asserted permission.
LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.
LinkDemand: Caller's Deny has no effect with LinkDemand-protected code.
LinkDemand: This Deny has no effect with LinkDemand-protected code.
```

## <a name="see-also"></a>Vedere anche

- <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
- <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)