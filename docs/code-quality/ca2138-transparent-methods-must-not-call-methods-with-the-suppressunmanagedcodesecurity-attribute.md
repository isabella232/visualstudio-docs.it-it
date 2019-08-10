---
title: "CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 316aef3b0f1f715857fde8eaf2a6e74b1a49e40f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920582"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
Un metodo trasparente per la sicurezza chiama un metodo contrassegnato con l' <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
Questa regola viene attivata su qualsiasi metodo trasparente che chiama direttamente nel codice nativo, ad esempio usando una chiamata P/Invoke (platform invoke). I metodi di interoperabilità P/Invoke e com contrassegnati <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> con l'attributo comportano l'esecuzione di un LinkDemand sul metodo chiamante. Poiché il codice trasparente per la sicurezza non è in grado di soddisfare I LinkDemand, il codice non può chiamare anche metodi contrassegnati con l'attributo SuppressUnmanagedCodeSecurity o metodi della classe contrassegnati con l'attributo SuppressUnmanagedCodeSecurity. Il metodo avrà esito negativo o la richiesta verrà convertita in una richiesta completa.

Le violazioni di questa regola conducono a <xref:System.MethodAccessException> nel modello di trasparenza della sicurezza di livello 2 e a una richiesta <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> completa per nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere l' <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo e contrassegnare il metodo con <xref:System.Security.SecurityCriticalAttribute> l' <xref:System.Security.SecuritySafeCriticalAttribute> attributo o.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]