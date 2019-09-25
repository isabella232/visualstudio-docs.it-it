---
title: 'CA2135: Gli assembly di livello 2 non devono contenere LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b9e7cb0eba06b00b30c2b7d00fac78206d222f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232237"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Gli assembly di livello 2 non devono contenere LinkDemand

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Una classe o un membro di classe utilizza <xref:System.Security.Permissions.SecurityAction> un oggetto in un'applicazione che utilizza la sicurezza di livello 2.

## <a name="rule-description"></a>Descrizione della regola
I LinkDemand sono deprecati nel set di regole per la sicurezza di livello 2. Anziché utilizzare i LinkDemand per applicare la sicurezza in fase di compilazione just-in-time (JIT), contrassegnare i metodi, i tipi e i <xref:System.Security.SecurityCriticalAttribute> campi con l'attributo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere <xref:System.Security.Permissions.SecurityAction> e contrassegnare il tipo o il membro con l' <xref:System.Security.SecurityCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente, l'oggetto <xref:System.Security.Permissions.SecurityAction> deve essere rimosso e il metodo contrassegnato con l' <xref:System.Security.SecurityCriticalAttribute> attributo.

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]