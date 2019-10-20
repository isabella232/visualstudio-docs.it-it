---
title: 'CA2143: i metodi Transparent non devono usare richieste di sicurezza | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bcfce9a80d02e525212d3f59173df4a7e8fbe968
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662696"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: I metodi Transparent non devono utilizzare SecurityDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo o un tipo tranparent è contrassegnato in modo dichiarativo con un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` richiesta o il metodo chiama il metodo <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola
 Il codice trasparente per la sicurezza non deve essere responsabile della verifica della sicurezza di un'operazione, pertanto non deve richiedere autorizzazioni. Il codice trasparente per la sicurezza deve usare richieste complete per prendere decisioni relative alla sicurezza e il codice critico per la sicurezza non deve basarsi sul codice trasparente per l'esecuzione della richiesta completa. Il codice che esegue controlli di sicurezza, ad esempio le richieste di sicurezza, deve essere invece critico per la sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 In generale, per correggere una violazione di questa regola, contrassegnare il metodo con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute>. È anche possibile rimuovere la richiesta.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 File delle regole nel codice seguente, perché un metodo trasparente esegue una richiesta di sicurezza dichiarativa.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Vedere anche
 [CA2142: Il codice Transparent non deve essere protetto con LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
