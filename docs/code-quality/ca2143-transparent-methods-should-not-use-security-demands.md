---
title: 'CA2143: I metodi Transparent non devono usare SecurityDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17160e5fd47491dddb22a28d4b3f7464ad3efb78
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914802"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: I metodi Transparent non devono usare SecurityDemand

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo trasparente o un metodo è contrassegnato in modo dichiarativo con un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` richiesta o il metodo chiama il <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> (metodo).

## <a name="rule-description"></a>Descrizione della regola
 Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Il codice trasparente per la sicurezza deve usare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa. Invece, qualsiasi codice che esegue controlli di sicurezza, ad esempio richieste di sicurezza, deve essere richiamabile da codice trasparente.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 In generale, per correggere una violazione di questa regola, contrassegnare il metodo con il <xref:System.Security.SecuritySafeCriticalAttribute> attributo. È anche possibile rimuovere la richiesta.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 La regola di file nel codice seguente, perché un metodo trasparente effettua una richiesta di sicurezza dichiarativa.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Vedere anche
 [CA2142: Il codice Transparent non deve essere protetto con LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)