---
title: "CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 1c05d8f6218166dc57e832412649bb04d9151f36
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549808"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity
|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo trasparente per la sicurezza chiama un metodo contrassegnato con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attributo.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola viene attivata in qualsiasi metodo trasparente che chiama direttamente nel codice nativo, ad esempio, tramite P/Invoke (PInvoke) chiamata. Metodi di interoperabilità P/Invoke e COM che sono contrassegnati con il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> comporterà un LinkDemand eseguito la chiamata al metodo dell'attributo. Poiché il codice SecurityTransparent non riesce a soddisfare i LinkDemand, il codice non è possibile chiamare anche i metodi contrassegnati con l'attributo SuppressUnmanagedCodeSecurity o i metodi della classe contrassegnata con l'attributo SuppressUnmanagedCodeSecurity. Il metodo avrà esito negativo o la richiesta verrà convertita in una richiesta completa.

 Le violazioni di questa regola conducono a un <xref:System.MethodAccessException> nel modello di trasparenza di sicurezza di livello 2 e una richiesta completa per <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> nel modello di trasparenza di livello 1.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> dell'attributo e contrassegnare il metodo con il <xref:System.Security.SecurityCriticalAttribute> o il <xref:System.Security.SecuritySafeCriticalAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]