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
ms.openlocfilehash: 9b05228ef22dee20506b728164d22976feb662ae
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945989"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Il codice Transparent non deve essere protetto con LinkDemand

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Richiede un metodo trasparente un <xref:System.Security.Permissions.SecurityAction> o un'altra richiesta di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su metodi trasparenti che richiedono a LinkDemands l'accesso. Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Poiché i metodi transparent avrebbero dovuto essere indipendente dalla sicurezza, essi devono prendere le decisioni relative alla sicurezza. Inoltre, il codice SafeCritical, quale prendere decisioni di protezione, non deve basarsi sul codice trasparente per apportate in precedenza questa decisione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere la richiesta di collegamento sul metodo trasparente o contrassegnare il metodo con <xref:System.Security.SecuritySafeCriticalAttribute> attributo se è in corso sicurezza controlli, ad esempio richieste di sicurezza.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, la regola viene attivata sul metodo perché il metodo è trasparente e contrassegnato con un LinkDemand <xref:System.Security.PermissionSet> che contiene un <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 Non escludere un avviso da questa regola.