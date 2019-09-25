---
title: 'CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cca385c346a7daa8aaddb377f999506ffb1abaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232047"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: I metodi Transparent non devono includere SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Category|Microsoft.Security|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un metodo trasparente, un metodo contrassegnato con il <xref:System.Security.SecuritySafeCriticalAttribute> metodo o un tipo che contiene un metodo è contrassegnato con l' <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola

I metodi decorati <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> con l'attributo hanno un LinkDemand implicito situato su qualsiasi metodo che lo chiama. Questo LinkDemand richiede che il codice che effettua la chiamata sia critico per la sicurezza. Contrassegnando il metodo che utilizza SuppressUnmanagedCodeSecurity con <xref:System.Security.SecurityCriticalAttribute> l'attributo, questo requisito risulta più ovvio per i chiamanti del metodo.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, contrassegnare il metodo o il tipo <xref:System.Security.SecurityCriticalAttribute> con l'attributo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

### <a name="code"></a>Codice

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]