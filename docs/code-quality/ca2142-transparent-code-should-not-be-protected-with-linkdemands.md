---
title: 'CA2142: Il codice Transparent non deve essere protetto con LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5bb8320a8876582cc325ecf973c83593777193
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920504"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Il codice Transparent non deve essere protetto con LinkDemand

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un metodo trasparente richiede una <xref:System.Security.Permissions.SecurityAction> o altre richieste di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
Questa regola viene attivata su metodi Transparent che richiedono l'accesso a I LinkDemand. Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Poiché i metodi Transparent sono considerati indipendenti dalla sicurezza, non devono prendere decisioni di sicurezza. Inoltre, il codice critico sicuro, che consente di prendere decisioni di sicurezza, non deve basarsi sul codice Transparent per avere preso in precedenza tale decisione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere la richiesta di collegamento sul metodo trasparente oppure contrassegnare il metodo <xref:System.Security.SecuritySafeCriticalAttribute> con l'attributo se esegue controlli di sicurezza, ad esempio le richieste di sicurezza.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente la regola viene attivata sul metodo perché il metodo è trasparente ed è contrassegnato con un LinkDemand <xref:System.Security.PermissionSet> che contiene un oggetto. <xref:System.Security.Permissions.SecurityAction>

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Non escludere un avviso da questa regola.