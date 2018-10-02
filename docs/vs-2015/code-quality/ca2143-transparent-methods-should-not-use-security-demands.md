---
title: 'CA2143: I metodi Transparent non devono utilizzare SecurityDemand | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed55d0645e70303f53bbd0d95021d05bb560fe23
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590016"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: I metodi Transparent non devono utilizzare SecurityDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2143: i metodi Transparent non devono utilizzare SecurityDemand](https://docs.microsoft.com/visualstudio/code-quality/ca2143-transparent-methods-should-not-use-security-demands).

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo trasparente o un metodo è contrassegnato in modo dichiarativo con un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` richiesta o il metodo chiama il <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> (metodo).

## <a name="rule-description"></a>Descrizione della regola
 Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Il codice trasparente per la sicurezza deve utilizzare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa. Invece, qualsiasi codice che esegue controlli di sicurezza, ad esempio richieste di sicurezza, deve essere richiamabile da codice trasparente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 In generale, per correggere una violazione di questa regola, contrassegnare il metodo con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo. È anche possibile rimuovere la richiesta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 La regola di file nel codice seguente, perché un metodo trasparente effettua una richiesta di sicurezza dichiarativa.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Vedere anche
 [CA2142: Il codice Transparent non deve essere protetto con LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)



