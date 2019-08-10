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
ms.openlocfilehash: 532a10740b0617f32e4f970da8dc2a7e2807f792
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920475"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: I metodi Transparent non devono usare SecurityDemand

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un metodo o un tipo tranparent è contrassegnato in modo dichiarativo con una <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` richiesta o <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> il metodo chiama il metodo.

## <a name="rule-description"></a>Descrizione della regola
Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Il codice trasparente per la sicurezza deve usare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa. Il codice che esegue controlli di sicurezza, ad esempio le richieste di sicurezza, deve essere invece critico per la sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
In generale, per correggere una violazione di questa regola, contrassegnare il metodo con <xref:System.Security.SecuritySafeCriticalAttribute> l'attributo. È anche possibile rimuovere la richiesta.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
File delle regole nel codice seguente, perché un metodo trasparente esegue una richiesta di sicurezza dichiarativa.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Vedere anche
[CA2142: Il codice Transparent non deve essere protetto con I LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)