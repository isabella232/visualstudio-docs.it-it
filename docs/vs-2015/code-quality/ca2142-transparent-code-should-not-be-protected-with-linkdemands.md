---
title: 'CA2142: Il codice Transparent non deve essere protetto con LinkDemand | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11bd1668e4ab599461d3619c63cd3c9732a05b4f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955795"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Il codice Transparent non deve essere protetto con LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Richiede un metodo trasparente un <xref:System.Security.Permissions.SecurityAction> o un'altra richiesta di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su metodi trasparenti di cui richiedono a LinkDemands l'accesso. Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Poiché i metodi transparent avrebbero dovuto essere indipendente dalla sicurezza, essi devono prendere le decisioni relative alla sicurezza. Inoltre, il codice SafeCritical, quale prendere decisioni di protezione, non deve basarsi sul codice trasparente per apportate in precedenza questa decisione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere la richiesta di collegamento sul metodo trasparente o contrassegnare il metodo con <xref:System.Security.SecuritySafeCriticalAttribute> attributo se è in corso sicurezza controlli, ad esempio richieste di sicurezza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente, la regola viene attivata sul metodo perché il metodo è trasparente e contrassegnato con un LinkDemand <xref:System.Security.PermissionSet> che contiene un <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Non escludere un avviso da questa regola.
