---
title: 'CA2142: il codice Transparent non deve essere protetto con I LinkDemand | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546432"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Il codice Transparent non deve essere protetto con LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente richiede una <xref:System.Security.Permissions.SecurityAction> o altre richieste di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola funziona su metodi trasparenti di cui richiedono a LinkDemands l'accesso. Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Poiché i metodi Transparent sono considerati indipendenti dalla sicurezza, non devono prendere decisioni di sicurezza. Inoltre, il codice critico sicuro, che consente di prendere decisioni di sicurezza, non deve basarsi sul codice Transparent per avere preso in precedenza tale decisione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere la richiesta di collegamento sul metodo trasparente oppure contrassegnare il metodo con l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo se esegue controlli di sicurezza, ad esempio le richieste di sicurezza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente la regola viene attivata sul metodo perché il metodo è trasparente ed è contrassegnato con un LinkDemand <xref:System.Security.PermissionSet> che contiene un oggetto <xref:System.Security.Permissions.SecurityAction> .

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Non escludere un avviso da questa regola.
